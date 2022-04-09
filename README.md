"# download-website-content" 


var html = document.getElementsByTagName('html')[0], download = function(pageId){
		req = new XMLHttpRequest();
        req.open('GET', ([document.location.protocol, document.location.host].join('//'))+"/?p="+pageId, true);
        req.addEventListener('load', function(e){
               	if (e.currentTarget.status != 200) return -1;
				try {
                    var title 	  = /\<title\>(.*?)\<\/title\>/.exec(e.target.response),
						filename  = /\/([a-zA-Z0-9\-\_]*)(\/$|$)/.exec(e.target.responseURL),
						text 	  = (title ? title[1] : filename[1])+'.html',
						a = document.createElement('a');
					 a.setAttribute('download', text+'.html');
					 a.textContent = text;
                     a.href='data:application/octet-stream,'+encodeURIComponent(e.target.response);
                     a.click();
					 html.appendChild(document.createElement('p'));
					 html.appendChild(a);
                } catch (e){ console.log(e); }

            })
	req.send();
};
html.textContent = "{ Dyrk.org } - Copie en cours, veuillez patienter / Dump .. please Wait : ";
for (var i=0;i<=1000;i++) setTimeout(download.bind(null, i), 250*i);


-------------------------------------------------------------------------------------------------------------------------------------------
Il  vous suffit d'aller sur le site à "dumper", et de balancer le script dans la console développeur (Touche F12, onglet "console")
Validez et patientez quelques secondes / minutes (selon la quantité de contenu du site)
