<!DOCTYPE html>
<html>
<head>
<script src="apts.js" type="text/javascript"></script>
</head>
<body onload="aptsLoad();">
<div id="conseils">
Attention à la gestion du temps : il s'agit d'un stage de 4 jours, avec des petits modules unitaires sur la seconde moitié de la semaine....
  <h3>Module 3</h3>
  Le lien de la vidéo sur Azure AD Connect Seamless SSO est faux et amène à une vidéo expliquant le SSO applicatif. Préférer le lien suivant : https://www.youtube.com/watch?v=PyeAC85Gm7w (Microsoft Mechanics).
  Ceci étant, vu le thème du module, il serait bien plus pertinent de parler à ce moment du SSO (et pas du "Seamless" SSO).
  <h3>Module 10</h3>
  OME a été remplçé par Purview Message Encryption (<a href="https://docs.microsoft.com/en-us/microsoft-365/compliance/ome-version-comparison?view=o365-worldwide#side-by-side-comparison-of-message-encryption-features-and-capabilities" target="_blank">comparaison</a>)
  A noter : <a href="https://docs.microsoft.com/en-us/microsoft-365/compliance/revoke-ome-encrypted-mail?view=o365-worldwide#encrypted-emails-that-you-can-revoke" target="_blank">Pas de révocation possible si message non consommé par le biais d'un lien</a>...
  <h3>Exemple de Timing (5 jours)</h3>
  <ul>
    <li>Jour 1 : Intro + modules 1 et 2
    <li>Jour 2 : Lab 2 + modules 3, 4 et 5
    <li>Jour 3 : Modules 6, 7 (sans lab) et 8
    <li>Jour 4 : Modules 9, 10 et 11
    <li>Jour 5 : Module 12 (sans lab), 13 et 14
  </ul>
  
  <h3>Exemple de Timing (4 jours)</h3>
  Le contenu est beaucoup trop riche pour être intégralement traité en 4 jours, il faudra faires des choix entre la théories/les échanges/les labs...
  <ul>
    <li>Jour 1 : Intro + modules 1 et 2
    <li>Jour 2 : modules 3, 4, 5 et 6
    <li>Jour 3 : 7 (sans lab),8, 9 et 10
    <li>Jour 4 : Modules 11, 12 (sans lab), 13 et 14
  </ul>
  

  <h3>Transition de terminologie</h3>
  <table><tr><th>Ancien</th><th>Nouveau</th><th>Objet</th></tr>
  <tr><td>Defender ATP</td><td>Defender for Endpoint</td><td>Cloud + Windows 10</td></tr>
  <tr><td>Office ATP</td><td>Defender For Office</td><td>Safe Links, Safe Attachements, ZAP etc...</td></tr>
  <tr><td>Azure ATP</td><td>Defender for Identity</td><td>Analyse hybride</td></tr>
  <tr><td>Azure ATA</td><td>Aucun</td><td>Fin de support => Transition vers Defender for Identity</td></tr>
  </table>
  
  Créer une nouvelle <a href="https://docs.microsoft.com/en-us/microsoft-365/compliance/create-a-custom-sensitive-information-type?view=o365-worldwide#create-a-custom-sensitive-information-type" target="_blank">Info sensible</a>
  
  <a href="https://docs.microsoft.com/en-us/mem/intune/enrollment/android-dedicated-devices-fully-managed-enroll" target="_blank">Android Enterprise & Intune</a>
  
  <a href="https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4VuQA" target="">Synthèse licenses business</a>
  
  <a href="https://m365maps.com/matrix.htm#000000000000000000000" target="_blank">Comparaison fonctionnelle (non officielle) licenses</a>
  
  <a href="https://docs.microsoft.com/en-us/microsoft-365/admin/basic-mobility-security/set-up?redirectSourcePath=%252fen-us%252farticle%252fManage-mobile-devices-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd&view=o365-worldwide" target="_blank">MDM for 365</a> (Basic MDM)
<div id="goDeploy"></div>
<div id="o365"></div>
</div>
</body>
</html>
