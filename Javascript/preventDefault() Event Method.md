## preventDefault() Event Method

###Prevent a link from opening the URL:
    
    document.getElementById("myAnchor").addEventListener("click", function(event){
      event.preventDefault()
    });
