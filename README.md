# Bootlint tools

Inspired by official [Bootlint project](https://github.com/twbs/bootlint) and bookmarklet.
Removes alert and adds a bit different styling.

## Chrome snippet

Copy and paste code below as new [Chrome Snippet](https://developer.chrome.com/devtools/docs/authoring-development-workflow#snippets).

```javascript
(function(){
    var scr = document.createElement("script"),
        titleStyle = "color: #fff; background: #6f5499; padding: 2px; font-size: 12px; margin: 5px 0;",
        wikiMessage = "for details, look up the lint problem IDs in the Bootlint wiki: " + 
          "https://github.com/twbs/bootlint/wiki\n" +
          "--------------------------------------------------------------------------------";
    
    console.log("%c%s", titleStyle, "Bootlint current page");
    console.info("Note: %c%s", "padding-top: 5px;", wikiMessage);
    
    scr.onload=function() {
        bootlint.lintCurrentDocument(function (problem) {
          console.warn("Bootlint: %c%s", "color: #fff; background: #d22;", problem.id, problem.message);
          console.log("Affected elements:", problem.elements, "\n ");
        }, []);
    };

    scr.src="https://maxcdn.bootstrapcdn.com/bootlint/latest/bootlint.min.js";
    document.body.appendChild(scr);
    return "";
})();
```

## Bookmarklet

[Bookmarklet installations info](https://en.wikipedia.org/wiki/Bookmarklet#Installation) on Wikipedia.

```javascript
javascript:(function(){var o=document.createElement("script"),t="color: #fff; background: #6f5499; padding: 2px; font-size: 12px; margin: 5px 0;",n="for details, look up the lint problem IDs in the Bootlint wiki: https://github.com/twbs/bootlint/wiki\n--------------------------------------------------------------------------------";console.log("%c%s",t,"Bootlint current page"),console.info("Note: %c%s","padding-top: 5px;",n),o.onload=function(){bootlint.lintCurrentDocument(function(o){console.warn("Bootlint: %c%s","color: #fff; background: #d22;",o.id,o.message),console.log("Affected elements:",o.elements,"\n ")},[])},o.src="https://maxcdn.bootstrapcdn.com/bootlint/latest/bootlint.min.js",document.body.appendChild(o)})();
```