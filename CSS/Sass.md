## CSS Extension & Description
- Nested Rules
```scss
.container{
   h1{
      font-size: 25px;
      color:#E45456;
   }
   
   p{
      font-size: 25px;
      color:#3C7949;
   }

   .box{
      h1{
         font-size: 25px;
         color:#E45456;
      }
      
      p{
         font-size: 25px;
         color:#3C7949;
      }
   }
}
```

- Referencing Parent Selectors
```scss
a {
   font-size: 20px;
   &:hover { background-color: yellow; }
}
```

- Nested Properties
```scss
.line {
   font: {
      family: Lucida Sans Unicode;
      size:20px;
      weight: bold;
      variant: small-caps;
   }
}
```
- Placeholder Selectors
```scss
.frst_para {
   color: green;
}
.sec_para {
   @extend .frst_para;
   font-size:20px;
}
```

- Variables
```scss
$txtcolor:#008000;
$fontSize: 20px;

p{
   color:$txtcolor;
   font-size:$fontSize;
}
```

- Mixin Arguments
```scss
@mixin bordered($color, $width: 2px) {
   color: #77C1EF;
   border: $width solid black;
   width: 450px;
}

.style  {
   @include bordered($color:#77C1EF, $width: 2px);
}
```
