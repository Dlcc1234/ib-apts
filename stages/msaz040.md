<!DOCTYPE html>
<html>
<head>
<script src="apts.js" type="text/javascript"></script>
</head>
<body onload="aptsLoad();">
<div id="conseils">
  Il s'agit bien d'une formation officielle, mais qui n'a pas de certification associée. Son contenu est orienté terrain et assez pragmatique !
  Lien vers les labs officiels MS sur Github : <a href="https://github.com/MicrosoftLearning/AZ-040T00-Automating-Administration-with-PowerShell/blob/master/Instructions/Labs" target="_blank">https://github.com/MicrosoftLearning/AZ-040T00-Automating-Administration-with-PowerShell/blob/master/Instructions/Labs</a>.
  
  <h3>Timing exemple</h3>
  <ul>
    <li>Jour 1 : Introduction + Learning Path 1 et 2</li>
    <li>Jour 2 : Learning path 3 et 4</li>
    <li>Jour 3 : Learning path 5, 6 et 7 modules  5, modules 1, 2, 3 et 4</li>
    <li>Jour 4 : Fin du Learning path 7, Learning path 8</li>
    <li>Jour 5 : Learning path 9, 10 et 11</li>
  </ul>
  <h3></h3>
  Exemple (a fin de démonstration, sans intérêt terrain) de renommage d'une propriété en sortie :  
  <span class='code'>Get-ComputerInfo | select @{l='ComputerName';e={$_.CSName}}|Get-Process</span>
  <h3>Tous les labs</h3>
  Les ateliers sur goDeploy sont <b>nécessaires</b> pour ce stage. Cependant, le dépot gitHub contient des ateliers (LAB_XX) et les corrigés d'atelier (LAB_AK_XX).
  Le contenu proposé par goDeploy correspond bien plus aux corrigés. Certains stagiaires préfèreront donc probablement une démarche de recherche personnelle avec les ateliers avant de regarder les corrigés, s'ils ont déjà des connaissances et le temps d'assumer cette démarche.
<div id=""goDeploy></div>
 <div id="Azure"></div>
</div>
</body>
</html>
