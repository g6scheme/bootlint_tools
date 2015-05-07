# Bootlint handy tools

Inspired by official [Bootlint project](https://github.com/twbs/bootlint) and bookmarklet.
Removes alert and adds a bit different styling.

## Chrome snippet

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