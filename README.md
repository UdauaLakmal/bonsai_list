# bonsai_list
bonsai used dropdown list sample 
var skiregions = 
{
    "glossary": {
        "title": "example glossary",
		"GlossDiv": {
            "title": "S",
			"GlossList": {
                "GlossEntry": {
                    "ID": "SGML",
					"SortAs": "SGML",
					"GlossTerm": "Standard Generalized Markup Language",
					"Acronym": "SGML",
					"Abbrev": "ISO 8879:1986",
					"GlossDef": {
                        "para": "A meta-markup language, used to create markup languages such as DocBook.",
						"GlossSeeAlso": ["GML", "XML"]
                    },
					"GlossSee": "markup"
                }
            }
        }
    }


};
function menuCreate(Jobject) {
function makeMenu(myregions, initTag) {
    if(!initTag){
    var html = "<ul  class='bonsai' >";
    }else{
    var html ="";
    }
    
    $.each(myregions,function(key,val){
    if (val == null) {
    val ="null"
    }
    if (val != null) {
       
        if (typeof val === "object"){
         html += "<li   class='has-children collapsed'> <div class='thumb'></div>";
         html += ""+key +":" + makeMenu(val,false);
         html += "</li>";
        }else{
           html += "<li> <div class='thumb'></div>";
           html += ""+key +": "+ val+",";
           html += "</li>";
        }
        }
    });
    if(!initTag)
    html += "</ul>";
    return html;
};


   var html = "<ol  class='bonsai' id ='silo_signals'>";
   if (typeof Jobject === "object")
           html += makeMenu(Jobject,true);
        else
           html += ""+Jobject;
   html += "</ol>";
    return html;
}
var menu = menuCreate(skiregions);
$(menu).appendTo("body");
