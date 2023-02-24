﻿<!DOCTYPE html>
<html>
<head>
<script src="apts.js" type="text/javascript"></script>
</head>
<body onload="aptsLoad();">
<div id="conseils">
Le contenu actuel du stage (Juillet 2021) a bien progressé depuis sa version initiale mais reste un peu léger pour 5 jours.
Il faudra éviter de prévoir des journées de travail trop dense : elles ne pourraient être remplies....
Il ne s'agit pas d'un stage d'introduction ou de <i>premier niveau</i> : Comme il prépare l'apprenant au métier d'administrateur Microsoft 365, il exige des prérequis non négligeables.
La terminologie des stages Microsoft a changé : les <i>Modules</i> et <i>Leçons</i> on été remplaçé par des <i>Learning Pathes</i> et <i>Modules</i> (attention à ce terme qui est malheureusement repris à un autre dessein).
Au vu des différences pédagigues entre les US et l'Europe, il pourra être pertinent de parler des <i>Check your knowledge</i> lors de l'apparition de la première diapositive puis de masquer les autres (Les diapositives "discussions" pourront également être remplaçées).
<h3>Timing exemple</h3>
<ul>
<li>Jour 1 : Modules 0, 1 et 2
<li>Jour 2 : Modules 3  et 4
<li>Jour 3 : Modules 5 et 6
<li>Jour 4 : Modules 7 et 8 (attention, pas de lab sur le module 8...)
<li>Jour 5 : Modules 9 et 10 (attention, pas de lab sur le module 9...)
</ul>
  <h3>Transition de terminologie</h3>
  Pour rappel, suite à l'arrivée de l'offre de sécurité globale Cloud MS "Defender", le nom des anciennes technologies qui ont été remplaçées:
  <table><tr><th>Ancien</th><th>Nouveau</th></tr>
  <tr><td>Defender ATP</td><td>Defender for Endpoint</td>/tr>
  <tr><td>Office ATP</td><td>Defender For Office</td></tr>
  <tr><td>Azure ATP</td><td>Defender for Identity</td><</tr>
  <tr><td>Azure ATA</td><td>Transition vers Defender for Identity</td></tr>
    <tr><td>Azure Information Protection</td><td>Microsoft Information Protection</td></tr>
  </table>
  <h3>Ateliers en général</h3>
  De nombreux points de latence importante sont présents : conseiller aux stagiaires de tirer parti du fait que les labs se suivent en testant les fonctionnalités qui ne marchent pas immédiatement la (demi)journée suivante.
 <h3>Lab 1</h3>
 <b>exercice 2</b>
 Si impossible de voir le rôle éligible dans la session de Patti, attendre et ressayer le lendemain : latence de mise en oeuvre de PIM sur certains tenants.
<h3>Module 3</h3>
 <a href="https://mslearn.cloudguides.com/en-us/guides/Protect%20and%20control%20information%20with%20Microsoft%20Cloud%20App%20Security" target="_blank">Interactive Guide complémentaire sur "CLoud App Security"</a>
 <a href="https://mslearn.cloudguides.com/guides/Investigate%20and%20remediate%20threats%20with%20Microsoft%20Defender%20for%20Endpoint" target="_blank">Interactive Guide complémentaire sur "Defender for Endpoint"</a>
<h3>Lab 5</h3>
Exercice 1, Tâche 1 A date (23/11/22) le "Important" est une mention oboslète (datant de l'époque ou l'on faisait des dlp dans le portail Exchange)
<h3>Lab 6</h3>
Exercice 1, tâche 3, point 21 : Dans la fenêtre de partage, bien remplacer les autorisations de "can Edit" à "can view"
<h3>Lab 7</h3>
L'exercice 2 est présent sur gitHub mais pas chez goDeploy...
<h3>Module 9</h3>
Pas de lab officiel, ce <a href="https://github.com/renaudwangler/ib/blob/master/extra/windowsAutopilot.md#lab--mise-en-place-dun-test-windows-autopilot" target="_blank">lab perso</a> pourra être proposé, an conseillant de le réaliser <b>après</b> tous les autres ateliers....  
<h3>Pour faire une démonstration de Office Message Encryption</h3>
Utiliser la commande suivante:
<code>Invoke-Command -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential (Get-Credential) -Authentication Basic -AllowRedirection -ScriptBlock {New-TransportRule -Name 'Office Message Encription  - Outside' -ApplyOME $true -ApplyRightsProtectionTemplate 'Encrypt' -SentToScope NotInOrganization}</code>
puis envoyer un message vers une boite externe à l'organisation Exchange
<div id="o365"></div>
<div id="goDeploy"></div>
</div>
</body>
</html>
