## 본격적으로 가변 그리드 배우기
- 가변 그리드 공식 이해하기 <br>
(가변 크기로 만들 박스의 가로 너비 ÷ 가변 크기로 만들 박스를 감싸고 있는 박스의 가로 너비) X 100 = 가변 크기의 값

### 서로 다른 크기의 박스를 가변 크기로 변환하기
```html
<div id="wrap">
    <div class="container">
        <div></div><div></div>
    </div>
</div>
```

```css
*{margin:0; padding:0;}

#wrap{
width:90%; /*가변*/
/* 960px */
height:500px;
margin:0 auto;
border:4px solid #000;
}

.container{
width:93.75%; /*가변*/
/* 960px / 900px */
height:492px;
margin:0 auto;
border:4px solid #000;
}

.container div{
display:inline-block;
height:100%;
}

.container div:first-child{
width:33.33333333333333%; /*가변*/
/* 300px ÷ 900px */
background:#1f518b;
}

.container div:first-child + div{
width:66.66666666666667%; /*가변*/
/* 600px ÷ 900px */
background:#f7e041;
}
```
#### 가변 패딩을 적용하는 두가지 방법
- 가변 패딩 적용 방법 1. 기본방법 <br>
(가변 패딩을 적용할 패딩값 ÷ 적용할 박스를 감싸고 있는 박스의 가로 너비) X 100 = 가변 패딩값
```html
<div id="wrap">
    <div></div><div></div>
</div>
```
```css
#wrap{
width:90%;
/* 960px */
height:500px;
margin:0 auto;
border:4px solid #000;
}

#wrap div{
width:31.25%;
/* 300px ÷ 960px */
height:100%;
display:inline-block;
}

#wrap div:first-child{
margin-right:37.5%;
/* 360px ÷ 960px */
background:#1f518b;
}

#wrap div:first-child + div{
background:#f7e041;
}
```
- 가변 패딩 적용 방법 2. 제한적인 조건이 있을때 <br>
(가변 패딩을 적용할 패딩값 ÷ 적용할 박스를 감싸고 있는 박스의 가로 너비) X 100 = 가변 패딩값
```html
<div id="wrap">
    <div></div><div></div>
</div>
```
```css
#wrap{
width:90%;
/* 960px */
height:500px;
margin:0 auto;
border:4px solid #000;
}

#wrap div{
width:31.25%;
/* 300px ÷ 960px */
display:inline-block;
}

#wrap div:first-child{
padding:50px 5.20833333333333%;
/* 50px ÷ 960px */
background:#1f518b;
}

#wrap div:first-child + div{
padding:130px 13.54166666666667%;
/* 130px ÷ 960px */
background:#f7e041;
}
```
- 고정 크기의 마진과 패딩을 위해 calc 함수 이용하기
```css
#wrap div{
width:calc(100% - 100px);
}
```