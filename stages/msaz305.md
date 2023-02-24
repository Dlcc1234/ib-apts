<!DOCTYPE html>
<html>
<head>
<script src="apts.js" type="text/javascript"></script>
</head>
<body onload="aptsLoad();">
<div id="conseils">
  Ce stage remplace le stage AZ-304  
  <a href="https://microsoftlearning.github.io/AZ-305-DesigningMicrosoftAzureInfrastructureSolutions/" target="_blank">Lien vers les études de cas stagiaires</a>
  <a href="https://github.com/microsoft/TailwindTraders" target="_blank">Mise en oeuvre applicative équivalente aux labs godeploy (complément au contenu).</a>
  <h3>Timing exemple</h3>
  <ul>
  <li>Jour 1 : Présentation du stage + Modules 1 (+ étude de cas) et 2 (+ études de cas 2 pour passer au jour 2)
  <li>Jour 2 : modules 3 (+ étude de cas), 4 et 5 (étud de cas 3 en fin de journée)
  <li>Jour 3 : Modules 6 (+ étude de cas), 7 et 8 (étude de cas 7)
  <li>Jour 4 : Débrief étude de cas 8 Fabrikam optionnelle, Modules 9 (+ étude de cas), 10 et 11 (sans études de cas)
  </ul>
  <h3>Module 7</h3>
  La diapositive N° 14 parle de l'IOT hub qui n'est pas repris dans le support skillpipe
  <a href="https://docs.microsoft.com/en-us/azure/architecture/icons/" target="_blank">Jeu d'icônes pour design Azure</a>  
  <div id="ateliers" class="grey">
  <h3 class="moins" onclick="switchDiv('ateliers-sub',this);">Ateliers goDeploy</h3>
  Les ateliers goDeploy sont à considérer comme un complément au stage (pour les participants les plus motivés).
  Le stage de 4 jours est taillé pour échanger autour des études de cas uniquement.  
  <div id="ateliers-sub" style="display: none;">
  Les ateliers goDeploy sont qualitatifs mais (très) longs (Particulièrement les ateliers 1, 2 et 6).
  <h3>Atelier 1</h3>
  L'exercie 1 commence par la création d'une VM de travail. En fait, dans la plateforme goDeploy, on utilisera directement la VM SEA-DEV fournie.
  Pour coller du code applicatif, il est préférable de passer par un collage dans un ficheir texte pour ne pas se faire avoir par les assistances à la complétion dans le portail/visual studio....
  <h4>Exercice 3</h4>Tâche 1, point 5 : "Command like arguments" est remplaçé par "application arguments"
  <h4>Exercice 5</h4>Tâche 1, point 12 : Choisir "outlook.com" et non "Office 365 - Outlook" si un compte live/outlook est utilisé.
  <h3>Atelier 2</h3>
  <h4>Exercice 3</h4>Si l'assistant de migration n'est pas correctement installé sur le serveur SQL, lancer son installation depuis c:\datamigrationassistant.msi.  
  <h4>Exercice 4</h3>Tâche 3, point 6: Vérifier que le profil de publication ne contient plus la chaine "{your_password}" mais le mot de passe de la base "Pawword.1!!" à la place...
  <h3>Atelier 6</h3>
  <h4>Exercice 7</h4>Tâche 2, point 3 : utiliser 192.168.1.0/27 comme espace d'adresses pour le sous-réseau de passerelle (il faudrea également modifier la taille de masque du réseau de passerelle de WGVnet1).
  
    </div></div>
<div id="Azure"></div>
</div>
</body>
</html>
