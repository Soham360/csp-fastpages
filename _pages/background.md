---
layout: page
permalink: /background/
title: Background
---

<style>
    body {
        font-family: "Courier New", Courier, monospace;
        font-size: 16px;
        color: #26FF00;
        background: black;
    }

    a {
        text-decoration:none;
        color: #26FF00;
    }

    a:hover {
        color: white;
    }

    ul {
        list-style-type: none;
        min-width: 100px;
    }

    li {
        float: left;
        padding-right: 100px;
    }

    #page-container {
        width: 1200px;
        text-align: left;
        margin: auto;
        margin-top: 50px;
    }

    #menu {
        display: table;
        margin: 0 0;
    }

    #content {
        padding-top: 10px;
        width: 700px;
        margin: 0 auto;
        display: block;
        clear: both;
    }

    #footer {
        width: 100%;
        text-align: center;
    }
</style>
<head>
    <meta charset="utf-8"> 
    <meta name="description" content="DUCHu.net - OSOBLIWE ROZWIAZANIA INTERNETOWE" />
    <title>DUCHu.net - OSOBLIWE ROZWIAZANIA INTERNETOWE</title>
    <meta name="keywords" content="html, javascript, ajax, php, java, c++, android, www, hosting, website, programmer, programista" />
    <meta name="author" content="DUCHu">
    <script type="text/javascript">
        onload = function() { textMatrix("logo"); }
    </script>
</head>
<body>
    <div id="page-container">
        <div id="logo">Loading...</div>
        <div id="footer"><a href="http://duchu.net" target="_blank">[ DUCHu ]</a></div>
    </div>
</body>
<script>
    var duch = "\
    %%%%%%%%%%%%%%%\.o######0o.<br>\
    %%%%%%%%%%%%%%0###########0.      .                                                                                  <br>\
    %%%%%%%%%%%%%o####\"^\"######0.    (## m#o   @@@@@@@  @@@  @@@  @@@@@@@ @@@  @@@ @@@  @@@    @@@  @@@ @@@@@@@@ @@@@@@@ <br>\
    %%%%%%%%%%%%%####(^^^^######0  ._ ##.##\"nn @@!  @@@ @@!  @@@ !@@      @@!  @@@ @@!  @@@    @@!@!@@@ @@!        @@!   <br>\
    %%%%%%%%%%%%%0####o^^^###\"^## (##o.######\" @!@  !@! @!@  !@! !@!      @!@!@!@! @!@  !@!    @!@@!!@! @!!!:!     @!!   <br>\
    %%%%%o00o.%%%%0#####o,##.^,#\"  \"#######(   !!:  !!! !!:  !!! :!!      !!:..!!! !!:  !!!    !!:  !!! !!:        !!:   <br>\
    %%%.0#####0.%%%0###########0     ########  ::.:..:   ::.:.:   ::.::.: .:.  :.:  ::.:.:  :: ::.  .:. :.::.:::   .:.   <br>\
    %%.0#######0.%%%\"0#########\"  _.o###\'\"00\"                                                                            <br>\
    %.0###########o._%\"\"################       _  .                                                                      <br>\
    %0####\"%\"#########################0      .0#0n0           DUCHu.net - OSOBLIWE ROZWIAZANIA INTERNETOWE               <br>\
    %#####.%%%\"\"#####################\"    _  0#####                                                                      <br>\
    %0#####.%%%%%\"###################._.o##o.#####\"                 Hosting, WWW, Facebook, Android                      <br>\
    %\"0#####..##mn%\"\"#############################                                                                       <br>\
    %%%\"0#######\"\"_%%%%\"\"##################\"#####\"                                                                       <br>\
    %%%%%%\"\"####m###m%%%%%%\"\"############\"   ####                                                                        <br>\
    %%%%%.########\"\"\"%%%%%%%%%.########\"     \"##\"                                                                        <br>\
    %%%%%####\"##\"###o%%%%%%%%(0######\"        \"\"                                                                         <br>\
    %%%%%\"##\".###,##%%%%%.o#o%\"\"####.                                                                    site: duchu.net <br>\
    %%%%%%%%%%\"##\"%%%%%%.0############.                                                                                  <br>\
    %%%%%%%%%%%%%%%%%%.n##RADIUS#######";             
    function textMatrix(container) {
        var str = duch;
        var ret = "";
        var tab = new Array(str.length);
        var spanS = "<span style=\"color:#2C2C2C\">";
        var spanSb = "<span style=\"color:#0F6700\">";
        var spanE = "</span>";
        for (var i = 0; i< str.length; i++) {
            if (str.charAt(i) == " " || str.charAt(i) == "^") tab[i] = randomLetter(1);
            else tab[i] = str.charAt(i);
        }
        var count = 0;
        var rets = "";
        var last = new Array(str.length);
    var interval = setInterval(function() {
        var rand = Math.floor(Math.random() * 100) + 70;
        var lote = new Array(rand);
        for (var i=0; i < rand; i++) {
            lote[i] = Math.floor(Math.random() * str.length);
            if (str.charAt(lote[i]) == " " || str.charAt(lote[i]) == "^") tab[lote[i]] = randomLetter(1);
        else {
                i--;
                continue;
            }
        }
        ret = "";						
        for (var i = 0; i < str.length; i++) {
            if (str.charAt(i) == " " || str.charAt(i) == "^") { 
                var change = false;
                for (var j = 0; j < rand; j++) {
                    if (lote[j] == i) {
                        if (str.charAt(i) == "^") ret += "<span style=\"color:red\">" + tab[i] + spanE;
                        else {
                            if ((Math.floor(Math.random() * 100) + 0) > 50) {
                    ret += "<span style=\"background:#090909;color:#2C2C2C;\">" + tab[i] + spanE;
                }
                            else ret += spanS + tab[i] + spanE;
                        }
                        change = true;
                        break;
                    }
                }
                if (!change) ret += spanS + tab[i] + spanE;
            } else if (str.charAt(i) == "%") ret += "&nbsp";
            else ret += str.charAt(i);
        }     
        document.getElementById(container).innerHTML = ret;
    }, 100); 
    }          
    function randomLetter(length) {
    var text = "";
    var possible = "abcdefghijklmnopqrstuvwxyz0123456789";
        for (var i = 0; i < length; i++) {
            text += possible.charAt(Math.floor(Math.random() * possible.length));
    }
        return text;
    }     
</script>