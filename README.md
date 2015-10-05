# cookiepolicy
A small JS script that you can paste into the bottom of your site so users can accept cookies on your site

For a short thing, include this before the </body> tag of your webpage. It is important to include it in the end!
For additional documentation, look into the index.html file

Include this script tag:
<script>
		   /*
			* You must include this line when using my plugin:
			* cookiepolicy.js created by Laszlo Levente Mári (twitter.com/noxowe)
			*/
			
			
			
			/* Declare translate variables in the fast and dirty way */
			var text=[], btnText=[], cookieNotice=[], moreInfoText=[], noticeText=[];
			
			/*
			 *	TRANSLATION TIME
			 *  ----------------
			 *  Please include the normal country flag (like en-US) and the first shortcut too (in this case 'en') for better browser support
			 *  So this is the translation skeleton that you can copy and modify:
			 *
			 *  text['en-US'] = 'A cookie notice text';
			 *  text['en'] = text['en-US'];
			 *  
			 *  Anyway, I think you should not modify the us text files
			 *  I included the Hungarian translation everywhere because I use it and as a scheme for you to add your own translation. 
			 *  So if you only want to change to one language and fallback to English, just change hu-HU and hu to your language codes
			 * 
			 *  Also, add your language to the list and remove Hungarian (if you don't want Hungarian translation) 
			 *  otherwise it will fall back to English language.
			 *
			 */
			var supportedLanguages = ['hu', 'hu-HU', 'en-US', 'en'];
			
			text['hu'] = 'Ez az oldal s&uuml;tiket tartalmaz.';
			text['hu-HU'] = text['hu'];
			text['en-US'] = 'This site contains cookies.';
			text['en'] = text['en-US'];
			
			
			btnText['hu'] = 'Elfogadom';
			btnText['hu-HU'] = btnText['hu'];
			btnText['en-US'] = 'I Agree';
			btnText['en'] = btnText['en-US'];
			
			
			noticeText['hu'] = "This site uses cookies – small text files that are placed on your machine to help the site provide a better user experience. In general, cookies are used to retain user preferences, store information for things like shopping carts, and provide anonymised tracking data to third party applications like Google Analytics. As a rule, cookies will make your browsing experience better. However, you may prefer to disable cookies on this site and on others. The most effective way to do this is to disable cookies in your browser. We suggest consulting the Help section of your browser or taking a look at <a href=\"http://www.aboutcookies.org\">the About Cookies website</a> which offers guidance for all modern browsers";
			noticeText['hu-HU'] = noticeText['hu'];
			noticeText['en-US'] = "This site uses cookies – small text files that are placed on your machine to help the site provide a better user experience. In general, cookies are used to retain user preferences, store information for things like shopping carts, and provide anonymised tracking data to third party applications like Google Analytics. As a rule, cookies will make your browsing experience better. However, you may prefer to disable cookies on this site and on others. The most effective way to do this is to disable cookies in your browser. We suggest consulting the Help section of your browser or taking a look at <a href=\"http://www.aboutcookies.org\">the About Cookies website</a> which offers guidance for all modern browsers";
			noticeText['en'] = noticeText['en-US'];
			
			
			moreInfoText['hu'] = 'Info';
			moreInfoText['hu-HU'] = moreInfoText['hu'];
			moreInfoText['en-US'] = 'Info';
			moreInfoText['en'] = moreInfoText['en-US'];
			


function createCookie(e,o,t){if(t){var i=new Date;i.setTime(i.getTime()+24*t*60*60*1e3);var n="; expires="+i.toGMTString()}else var n="";document.cookie=e+"="+o+n+"; path=/"}function readCookie(e){for(var o=e+"=",t=document.cookie.split(";"),i=0;i<t.length;i++){for(var n=t[i];" "==n.charAt(0);)n=n.substring(1,n.length);if(0==n.indexOf(o))return n.substring(o.length,n.length)}return null}function CPModal(){el=document.getElementById("cpoverlay"),el.style.visibility="visible"==el.style.visibility?"hidden":"visible"}function CPAccept(){if("yes"==window.iscookie)console.log("ERROR. How u do dat.");else{{createCookie("CookiePolicyAccepted","yes")}document.getElementById("cookiepolicy").setAttribute("style","display:none;")}}window.iscookie=readCookie("CookiePolicyAccepted");var language=window.navigator.userLanguage||window.navigator.language;supportedLanguages.indexOf(language)>-1||(language="en-US"),console.log(language),cookieNotice["en-US"]='<div style="width: 600px; margin: 100px auto; background-color: #eee; border: 1px solid #000; padding: 15px; text-align: center;"><h1>Cookie Policy</h1><p>'+noticeText[language]+"</p>Click here to [<a href='#' onclick='CPModal()'>close</a>]</div>",cookieNotice.en=cookieNotice["en-US"],cookieNotice["hu-HU"]='<div style="width: 600px; margin: 100px auto; background-color: #eee; border: 1px solid #000; padding: 15px; text-align: center;"><h1>Cookie Policy</h1><p>'+noticeText[language]+"</p>[<a href='#' onclick='CPModal()'>Bezárás</a>]</div>",cookieNotice.hu=cookieNotice["hu-HU"];var cookiecontainer=document.createElement("div");cookiecontainer.setAttribute("id","cookiepolicy"),cookiecontainer.setAttribute("style",'font-size: 1em; line-height: 1.6; font-weight: 400; font-family: HelveticaNeue,"Helvetica Neue",Helvetica,Arial,sans-serif; color: #222; top: 0px; width: 60%; height: 60px; background: #EEE none repeat scroll 0% 0%; border-bottom: 1px solid #C5C2C2; margin: 0px; padding: 0px 20% 0px 20%; position: absolute; display: block; max-width: 100%;');var cookieModal=document.createElement("div");cookieModal.setAttribute("id","cpoverlay"),cookieModal.setAttribute("style","visibility: hidden;position: absolute;left: 0px;top: 0px;width:100%;height:100%;text-align:center;z-index: 1000;"),cookieModal.innerHTML=cookieNotice[language];var insideText=document.createElement("p");insideText.setAttribute("style","display: inline-block;padding: 17px;margin-bottom: 2.5rem;margin-top: 0px;"),insideText.innerHTML=text[language],cookiecontainer.appendChild(insideText);var moreinfo=document.createElement("a");moreinfo.setAttribute("style","float: right; padding: 17px; color: #1EAEDB; cursor: pointer; text-decoration: underline;"),moreinfo.setAttribute("onclick","CPModal()"),moreinfo.innerHTML=moreInfoText[language],cookiecontainer.appendChild(moreinfo);var acceptbtn=document.createElement("a");if(acceptbtn.setAttribute("style","float: right; padding: 17px; color: #1EAEDB; cursor: pointer; text-decoration: underline;"),acceptbtn.setAttribute("onclick","CPAccept()"),acceptbtn.innerHTML=btnText[language],cookiecontainer.appendChild(acceptbtn),"yes"==window.iscookie)console.log("cool, you accepted cookies. Thanks!");else{var body=document.getElementsByTagName("body")[0];body.setAttribute("style","margin:0;padding-top:60px;"),body.appendChild(cookiecontainer),body.appendChild(cookieModal)}
</script>