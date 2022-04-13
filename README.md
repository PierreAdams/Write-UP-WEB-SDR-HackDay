# Write-UP-WEB-SDR-HackDay
Dans ce Writeup, je vous explique comment j'ai réussi à flag le challenge WebSDR du ctf Hackday  
https://hackday.fr/


<img width="400" alt="Capture d’écran 2022-04-13 à 15 19 06" src="https://user-images.githubusercontent.com/39098396/163189411-4b3035a6-22a9-434a-8daf-92e0781c2fc6.png">

Ce chall ne fourni ni fichier ni ip/port pour du tcp, mais le titre donne un indice "WebSDR" :  
Un WebSDR est un récepteur radio accesible sur Internet, nous permettant ainsi d'écouteur et d'analyser certains signaux sans forcément avoir le materiel nécessaire. 
Certain site web comme http://websdr.org/ permet de les lister 

Le challenge est hebergé par ESIEE Paris donc une plateforme francais, il conviendra donc de selectionner un websdr hebergé proche de paris : 
celle ci par exemple : http://dk0te.dhbw-ravensburg.de:8901/

<img width="984" alt="Capture d’écran 2022-04-13 à 16 01 04" src="https://user-images.githubusercontent.com/39098396/163197774-5cc4130d-c32d-46b4-89c6-7e4b99ad9aab.png">

En journée, le signal va etre moins audible voir quasi inexistant en cas de forte température. Ce sont les lois de la Propagation ionosphérique, ainsi, il vaut mieux écouter le signal en début de soirée. (Comme le dis l'énoncée : A la nuit tombée, tout s'éclaire)

