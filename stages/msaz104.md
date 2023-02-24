﻿<!DOCTYPE html>
<html>
<head>
<script src="apts.js" type="text/javascript"></script>
</head>
<body onload="aptsLoad();">
<div id="conseils">
  Le stage est plutôt dense sur 4 jours et s'adresse à des stagiaires qui ont impérativement suivi le msaz900 pour connaitre les principes Cloud et Azure de base.
  Le cas échéant, renvoyer les stagiaires sur le az-900 sur MSLearn.
<h3>En direct du <a href="https://learningdownloadcenter.microsoft.com/" target="_blank">Learning Download Center</a></h3>
  Dans les éléments téléchargeables concernant ce stage, ne pas passer à côté de :
  <ul>
    <li>Le "Course Datasheet" qui contient des relations entre le contenu du stage en salle et les liens MSLearn correspondant.</li>
    <Li>Le fichier "Demonstrations" qui, comme son nom l'indique, contient le déroulé des diverses démonstrations utilisées dans le stage.</li>
    <li>Le fichier "AssessmentGuide" qui comprend des liens afin de créer des formulaires/QCM pour chaque module et de les partager aux stagiaires (particulièrement pertinent poru de l'animation distancielle).
    <li>Un changelog très complet.</li>    
  </ul>
  <h3>Timing exemple</h3>
  <ul>
    <li>Jour 1 : Introduction modules 1 et 2</li>
    <li>Jour 2 : Modules 3,4 et 5</li>
    <li>Jour 3 : Modules 6, 7 et 8</li>
    <li>Jour 4 : Modules 9, 10 et 11</li>
  </ul>
  <h3>Tous les labs</h3>
  Les ateliers *goDeploy* ne sont pas nécessaires (voire pénalisant pour la partie Azure AD) avec ce stage.
  
  Si les stagiaires ont des problèmes, par exemple pour se connecter en RDP à une machine virtuelle, on purra se référer aux <a href="https://github.com/renaudwangler/ib/blob/master/extra/ibAzureLabs.md#mise-en-place-dun-environnement-dateliers-ib-sur-un-compte-azure" target="_blank">procédures de mise en place d'un environnement d'ateliers ib sur un compte Azure</a>!
  
  Lien vers <a href="https://microsoftlearning.github.io/AZ-104-MicrosoftAzureAdministrator/" target="_blank">les labs az-104 sur Github</a> (qui sont illustrés.)
  Il existe désormais une <a href="" target="_blank">traduction française</a> (probablement automatique des ateliers).
  A voir aussi : <a href="https://mslabs.cloudguides.com/guides/AZ-104%20Exam%20Guide%20-%20Microsoft%20Azure%20Administrator" target="_blank">Simulation intéractive de tous les ateliers az-104</a>.
  
  Expliquer la procédure de nettoyage consistant à supprimer le Resource Group, souvent plus pertinente que les commandes fournies.
  
  <h3>Atelier 2</h3>
  Pour les stagiaires ayant utilisé la <b>procédures de mise en place d'un environnement d'ateliers ib sur un compte Azure</b>, la stratégie (AZure Policy) travaillera sur le resource group <i>ibLabs</i> qui est vérouillé : inviter à supprimer le verrou (<i>lock</i>) pour faire le ménage des stratégies.
 
  <h3>Atelier 5</h3>
  Pour éviter les limitations du Pass Azure, conseiller les régions <b>eastus</b> et <b>westus</b> (et rappeler que les crochets <b>[</b> et <b>]</b> ne sont pas à conserver.
  
   
  <h3>Atelier 6</h3>
  Il semblerait que, de manière aléatoire, le "network watcher" pose des problèmes dans certaines régions avec les limitations des Pass azure...  
  Voici un code Powershell permettant de réaliser les test Network Watcher dans tous les cas : 
  <code>$rgName = "az104-06-rg1"
    echo 'getting VMs'' informations.'; $VMs=@();$tests=@();$results=@();Get-AzVM -ResourceGroupName $rgName|ForEach-Object {$vms+=[pscustomobject]@{name=$_.name;location=$_.location;id=$_.id;ip=(Get-AzNetworkInterface -ResourceId ($_.networkprofile.networkInterfaces[0].id)).IpConfigurations[0].PrivateIpAddress}}
    $VMNum=$VMs.count*($VMs.count-1); $i=1; foreach ($vmSource in $VMs) {foreach ($vmDest in $VMs) {if ($vmSource.name -ne $vmDest.name) { Write-Progress -Activity "Launching tests" -Status "$($vmSource.name) to $($vmDest.name)" -PercentComplete ($i/$VMNum*100);$i++;$tests+=[pscustomobject]@{sourceVM=$vmSource.name;destinationVM=$vmDest.name;destinationIP=$vmDest.ip;job=Test-AzNetworkWatcherConnectivity -NetworkWatcher (Get-AzNetworkWatcher|Where-Object -Property Location -eq $vmSource.location) -SourceId $vmSource.id -DestinationAddress $vmDest.ip -DestinationPort 3389 -AsJob}}}}
    $i=1; foreach ($test in $tests) {Write-Progress -Activity "Waiting for results" -Status "$($test.sourceVM) to $($test.destinationVM)" -PercentComplete ($i/$VMNum*100);$i++; While ($test.job.state -notlike 'completed') {Start-Sleep -s 15}; $results+=[pscustomobject]@{sourceVM=$test.sourceVM;targetVM=$test.destinationVM;targetIP=$test.destinationIP;targetPort='3389';result=$test.job.output.connectionStatus;latency=$test.job.output.avglatencyinms}}
    $results|format-table</code>
  S'il est impossible d'ajouter une table de routage à un subnet depuis ladite table (latence d'affichage), essayer de passer par l'édtion du dubnet...  
  Voici un code Powershell pour réaliser le loadBalancer si les vNet tardent à remonter dans l'interface du portail:
  <code>$publicip=New-AzPublicIpAddress -Name 'az104-06-pip4' -ResourceGroupName 'az104-06-rg1' -Location (Get-AzResourceGroup -Name 'az104-06-rg1').location -Sku standard -AllocationMethod static
$frontIp = New-AzLoadBalancerFrontendIpConfig -Name 'frontEnd' -PublicIpAddress $publicIp;$bepool = New-AzLoadBalancerBackendAddressPoolConfig -Name 'az104-06-lb4-be1';$probe = New-AzLoadBalancerProbeConfig -Name 'az104-06-lb4-hp1' -Protocol tcp -Port 80 -IntervalInSeconds 5 -ProbeCount 2;$lbRule = New-AzLoadBalancerRuleConfig -Name 'az104-06-lb4-lbrule1' -Protocol tcp -FrontendPort 80 -BackendPort 80 -IdleTimeoutInMinutes 4 -FrontendIpConfiguration $frontIp -BackendAddressPool $bePool -EnableTcpReset -DisableOutboundSNAT
New-AzLoadBalancer -ResourceGroupName 'az104-06-rg1' -Name 'az104-06-lb4' -Location (Get-AzResourceGroup -Name 'az104-06-rg1').location -Sku Standard -FrontendIpConfiguration $frontIp -BackendAddressPool $bePool -LoadBalancingRule $lbRule -Probe $probe
$bepool = get-AzLoadBalancerBackendAddressPool -ResourceGroupName 'az104-06-rg1' -LoadBalancerName 'az104-06-lb4' -Name 'az104-06-lb4-be1'
$vNet = Get-AzVirtualNetwork -Name 'az104-06-vnet01' -ResourceGroupName 'az104-06-rg1';$ip0 = New-AzLoadBalancerBackendAddressConfig -IpAddress "10.60.0.4" -Name "az104-06-vm0" -VirtualNetworkid $vNet.id;$ip1 = New-AzLoadBalancerBackendAddressConfig -IpAddress "10.60.1.4" -Name "az104-06-vm1" -VirtualNetworkid $vNet.id;$bepool.LoadBalancerBackendAddresses.Add($ip0);$bepool.LoadBalancerBackendAddresses.Add($ip1);Set-AzLoadBalancerBackendAddressPool -InputObject $bepool</code>
  Voici un code Powershell pour réaliser l'Application Gateway si problème avec affichage des vNet dans le protail :
  <code>$vNet = Get-AzVirtualNetwork -Name 'az104-06-vnet01' -ResourceGroupName 'az104-06-rg1'; $subnetConfig = Add-AzVirtualNetworkSubnetConfig -Name 'subnet-appgw' -virtualNetwork $vNet -AddressPrefix '10.60.3.224/27'; $vNet| Set-AzVirtualNetwork; $pip = New-AzPublicIpAddress -ResourceGroupName az104-06-rg1 -Location eastus -Name az104-06-pip5 -AllocationMethod Dynamic; $subNet = $vnet.Subnets|where name -eq subnet-appgw
$gipconfig = New-AzApplicationGatewayIPConfiguration -Name myAGIPConfig  -Subnet $subnet ; $fipconfig = New-AzApplicationGatewayFrontendIPConfig  -Name myAGFrontendIPConfig -PublicIPAddress $pip; $frontendport = New-AzApplicationGatewayFrontendPort -Name myFrontendPort -Port 80; $defaultPool = New-AzApplicationGatewayBackendAddressPool -Name az104-06-appgw5-be1 -BackendIPAddresses '10.62.0.4', '10.63.0.4';$poolSettings = New-AzApplicationGatewayBackendHttpSettings -Name az104-06-appgw5-http1 -Port 80 -Protocol Http -CookieBasedAffinity Enabled -RequestTimeout 20; $defaultlistener = New-AzApplicationGatewayHttpListener -Name az104-06-appgw5-rl1l1 -Protocol Http -FrontendIPConfiguration $fipconfig -FrontendPort $frontendport; $frontendRule = New-AzApplicationGatewayRequestRoutingRule -Name az104-06-appgw5-rl1  -RuleType Basic -HttpListener $defaultlistener -BackendAddressPool $defaultPool -BackendHttpSettings $poolSettings; $sku = New-AzApplicationGatewaySku -Name WAF_Medium -Tier WAF -Capacity 2
$appgw = New-AzApplicationGateway -Name az104-06-appgw5  -ResourceGroupName az104-06-rg1  -Location eastus -BackendAddressPools $defaultPool  -BackendHttpSettingsCollection $poolSettings -FrontendIpConfigurations $fipconfig -GatewayIpConfigurations $gipconfig -FrontendPorts $frontendport -HttpListeners $defaultlistener -RequestRoutingRules $frontendRule -Sku $sku </code>
  <h3>Atelier 7</h3>
  Dans l'exercice 1, tâche 5 on utilise le "<i>Run command</i>" de la paravirtualisation Azure pour faire un new-PSDrive en powershell. Si le nom du storage account créé précédemment <u>commence par un n</u> le binôme de caractères "<b>\n</b>" pourra être interprété comme un retour à la ligne....
  
  <h3>Module 9</h3>
  Il pourra être pertinent de faire une double-démonstration :
  <ul>
    <li> Créer une Web-App avec un conteneur Docker "nginx" récupéré depuis le Docker Hub</li>
    <li> Créer une instance de conteneur "nginx" récupérée depuis le Docker Hub</li>
  </ul>
  Cela permet de bien montrer la différence entre les deux approches, la gestion applicative complète PAAS de la web-app et le '<i>quasi-Iaas</i>' de l'instance de conteneur.
  <h3>Atelier 10</h3>
  A noter que si l'on crée un <b>Log Analytics</b> en "East US", le <b>Automation Account</b> derva être créé dans la région "East US 2" (et vice versa, comme indiqué dans le document pointé par la petite note de l'atelier).
  <div id="Azure"></div>
</div>
</body>
</html>
