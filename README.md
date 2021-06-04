<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Twitter Tweet Box Sparsh Kharya</title>
  <link rel="stylesheet" href="style.css">
  <link rel="stylesheet" href="https://unicons.iconscout.com/release/v3.0.6/css/line.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"/>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600;700&display=swap');
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Open Sans', sans-serif;
}
body{
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background: #1da1f2;
}
::selection{
  color: #fff;
  background: #1da1f2;
}
.wrapper{
  background: #fff;
  max-width: 475px;
  width: 100%;
  border-radius: 15px;
  padding: 25px 25px 15px 25px;
  box-shadow: 0px 10px 15px rgba(0,0,0,0.1);
}
.input-box{
  padding-top: 10px;
  border-bottom: 1px solid #e6e6e6;
}
.input-box .tweet-area{
  position: relative;
  min-height: 130px;
  max-height: 170px;
  overflow-y: auto;
}
.tweet-area::-webkit-scrollbar{
  width: 0px;
}
.tweet-area .placeholder{
  position: absolute;
  margin-top: -3px;
  font-size: 22px;
  color: #98A5B1;
  pointer-events: none;
}
.tweet-area .input{
  outline: none;
  font-size: 17px;
  min-height: inherit;
  word-wrap: break-word;
  word-break: break-all;
}
.tweet-area .editable{
  position: relative;
  z-index: 5;
}
.tweet-area .readonly{
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  color: transparent;
  background: transparent;
}
.readonly .highlight{
  background: #fd9bb0;
}
.input-box .privacy{
  color: #1da1f2;
  margin: 15px 0;
  display: inline-flex;
  align-items: center;
  padding: 7px 10px;
  border-radius: 50px;
  cursor: pointer;
  transition: background 0.2s ease;
}
.privacy:hover, .icons li:hover{
  background: #e7f5fe;
}
.privacy i{
  font-size: 18px;
}
.privacy span{
  font-size: 15px;
  font-weight: 600;
  margin-left: 7px;
}
.bottom{
  display: flex;
  margin-top: 13px;
  align-items: center;
  justify-content: space-between;
}
.bottom .icons{
  display: inline-flex;
}
.icons li{
  list-style: none;
  color: #1da1f2;
  font-size: 20px;
  margin: 0 2px;
  height: 38px;
  width: 38px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  transition: background 0.2s ease;
}
.bottom .content{
  display: flex;
  align-items: center;
  justify-content: center;
}
.bottom .counter{
  color: #333;
  display: none;
  font-weight: 500;
  margin-right: 15px;
  padding-right: 15px;
  border-right: 1px solid #aab8c2;
}
.bottom button{
  padding: 9px 18px;
  border: none;
  outline: none;
  border-radius: 50px;
  font-size: 16px;
  font-weight: 700;
  background: #1da1f2;
  color: #fff;
  cursor: pointer;
  opacity: 0.5;
  pointer-events: none;
  transition: background 0.2s ease;
}
.bottom button.active{
  opacity: 1;
  pointer-events: auto;
}
.bottom button:hover{
  background: #0d8bd9;
}
<style>
</head>
<body>
  <h1>Twitter Tweet Box with Html, CSS & JAVASCRIPT </h1>
  <div class="wrapper">
    <div class="input-box">
      <div class="tweet-area">
        <span class="placeholder">What's happening?</span>
        <div class="input editable" contenteditable="true" spellcheck="false"></div>
        <div class="input readonly" contenteditable="true" spellcheck="false"></div>
      </div>
      <div class="privacy">
        <i class="fas fa-globe-asia"></i>
        <span>Everyone can reply</span>
      </div>
    </div>
    <div class="bottom">
      <ul class="icons">
        <li><i class="uil uil-capture"></i></li>
        <li><i class="far fa-file-image"></i></li>
        <li><i class="fas fa-map-marker-alt"></i></li>
        <li><i class="far fa-grin"></i></li>
        <li><i class="far fa-user"></i></li>
      </ul>
      <div class="content">
        <span class="counter">100</span>
        <button>Tweet</button>
      </div>
    </div>
  </div>
  <footer>
    <span>Created By <a href="#">SparshKharya</a> | <span class="far fa-copyright"></span> 2021 All rights reserved.</span>
</footer>
<script>
  const wrapper = document.querySelector(".wrapper"),
editableInput = wrapper.querySelector(".editable"),
readonlyInput = wrapper.querySelector(".readonly"),
placeholder = wrapper.querySelector(".placeholder"),
counter = wrapper.querySelector(".counter"),
button = wrapper.querySelector("button");

editableInput.onfocus = ()=>{
  placeholder.style.color = "#c5ccd3";
}
editableInput.onblur = ()=>{
  placeholder.style.color = "#98a5b1";
}

editableInput.onkeyup = (e)=>{
  let element = e.target;
  validated(element);
}
editableInput.onkeypress = (e)=>{
  let element = e.target;
  validated(element);
  placeholder.style.display = "none";
}

function validated(element){
  let text;
  let maxLength = 100;
  let currentlength = element.innerText.length;

  if(currentlength <= 0){
    placeholder.style.display = "block";
    counter.style.display = "none";
    button.classList.remove("active");
  }else{
    placeholder.style.display = "none";
    counter.style.display = "block";
    button.classList.add("active");
  }

  counter.innerText = maxLength - currentlength;

  if(currentlength > maxLength){
    let overText = element.innerText.substr(maxLength); //extracting over texts
    overText = `<span class="highlight">${overText}</span>`; //creating new span and passing over texts
    text = element.innerText.substr(0, maxLength) + overText; //passing overText value in textTag variable
    readonlyInput.style.zIndex = "1";
    counter.style.color = "#e0245e";
    button.classList.remove("active");
  }else{
    readonlyInput.style.zIndex = "-1";
    counter.style.color = "#333";
  }
  readonlyInput.innerHTML = text; //replacing innerHTML of readonly div with textTag value
}
  <script>
  <script src="script.js"></script>
</body>
</html>
