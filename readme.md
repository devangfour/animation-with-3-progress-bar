
### HTML

```
<div class="section-progress">
        <div class="">
            <div class="progress progressbar-1 start-progress">
                <div class="progress-value"></div>
                <div class="progress-per"></div>
            </div>
            <div class="progress progressbar-2">
                <div class="progress-value"></div>
                <div class="progress-per"></div>
            </div>
            <div class="progress progressbar-3">
                <div class="progress-value"></div>
                <div class="progress-per"></div>
            </div>
        </div>
        <div class="progress-round">
            <div class="round round-1"></div>
            <div class="round round-2"></div>
            <div class="round round-3"></div>
        </div>
    </div>
```

### CSS
```
.section-progress {
    justify-content: center;
    align-items: center;
    background: #000;
    display: flex;
    height: 100vh;
    padding: 0;
    margin: 0;
}

.progress {
    background: rgba(255, 255, 255, 0.1);
    justify-content: flex-start;
    border-radius: 100px;
    align-items: center;
    position: relative;
    padding: 0 5px;
    display: flex;
    height: 40px;
    width: 500px;
    margin-bottom: 10px;
}
.progress.start-progress .progress-value {
    animation: load 3s normal forwards;
    box-shadow: 0 10px 40px -10px #fff;
    border-radius: 100px;
    background: #fff;
    height: 30px;
    width: 0;
}

.progress:not(.start-progress){
    height: 10px;
}
.progress-per {
    color: #fff;
    margin: 0 auto;
}

@keyframes load {
    0% {
        width: 0;
    }

    100% {
        width: 100%;
    }
}
.progress-round{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
.progress-round .round{
    margin: 0 auto;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: aqua;
    position: relative;
}
.progress-round .round.done{
    background-color: #fff;
}
.progress-round .round.done:after{
    position: absolute;
    content: "✔️";
}
```

### Javascript
```
function setProgressBar(element){
    var percentage = 0;
    var progressBarInterval = setInterval(function(){
        if(percentage == 101){
            clearInterval(progressBarInterval);
        }else{
            element.innerHTML  = percentage +'%';
            percentage = percentage + 1;
        }
    },33);
}
var currentProgressbar = 1;
setProgressBar(document.querySelector('.progressbar-1 .progress-per'));
var progressbarInterval = setInterval(function(){
    document.querySelector('.progressbar-'+currentProgressbar).classList.remove('start-progress');
    document.querySelector('.round-'+currentProgressbar).classList.add('done');
    currentProgressbar = currentProgressbar + 1;

    if(!document.querySelector('.progressbar-'+currentProgressbar)){
        window.location.href = 'https://google.com';
    }
    
    document.querySelector('.progressbar-'+currentProgressbar).classList.add('start-progress');
    setProgressBar(document.querySelector('.progressbar-'+currentProgressbar + ' .progress-per'));
},3300);
```