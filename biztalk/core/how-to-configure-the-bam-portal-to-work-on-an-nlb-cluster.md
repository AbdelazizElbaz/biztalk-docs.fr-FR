---
title: "Comment configurer le portail BAM pour travailler sur un Cluster d’équilibrage de charge réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96c04fde-dc12-42fb-9193-aa74819fe880
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73bd5013cd2a09d240fa58b7cf5283c8d1903c69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster"></a>Configuration du portail BAM de sorte qu'il fonctionne dans un cluster NLB
Le portail BAM peut être configuré pour fonctionner dans un cluster d'équilibrage de charge réseau.  
  
> [!IMPORTANT]
>  Portail BAM *uniquement* s’exécute en mode 32 bits. Si IIS est installé sur un ordinateur 64 bits, vérifiez qu’ASP.NET 2.0 est activé en mode 32 bits. Pour ce faire, ouvrez le Gestionnaire des services Internet, ouvrez **Pool d’applications**, sélectionnez le pool d’applications (BAMAppPool), puis cliquez sur **paramètres avancés**. Dans **Activer les applications 32 bits**, sélectionnez **True**.  
>   
>  Pour les logiciels supplémentaires requis du portail BAM, consultez [planification pour le portail BAM](../core/planning-for-the-bam-portal.md).  
  
### <a name="to-prepare-to-configure-bam-portal-on-an-nlb-cluster"></a>Pour préparer la configuration du portail BAM dans un cluster d'équilibrage de charge réseau  
  
1.  Installez et configurez le portail sur le premier ordinateur.  
  
    > [!NOTE]
    >  Configurez le portail uniquement sur le premier ordinateur. Vous avez la possibilité d'activer le portail BAM sur les autres ordinateurs du cluster, mais la configuration ne doit être effectuée que sur le premier.  
  
2.  Installez les composants du portail sur tous les ordinateurs à inclure dans le cluster d'équilibrage de charge réseau, puis joignez les autres ordinateurs du cluster dans le groupe BizTalk de l'ordinateur sur lequel le portail est configuré. Vous devez activer les groupes BizTalk et joindre le groupe approprié.  
  
3.  Sélectionnez la base de données de gestion BizTalk configurée pour l'ordinateur sur lequel le portail est installé.  
  
4.  Créez le cluster d'équilibrage de charge réseau. Pour plus d’informations sur la façon de créer et gérer des clusters d’équilibrage de la charge réseau, consultez « Créer et gérer charger Clusters d’équilibrage réseau » à [http://go.microsoft.com/fwlink/?LinkId=56206](http://go.microsoft.com/fwlink/?LinkId=56206).  
  
    > [!NOTE]
    >  Vous devez vérifier que le cluster d'équilibrage de charge réseau fonctionne correctement hors du contexte de BizTalk Server avant de poursuivre.  
  
    > [!NOTE]
    >  Pour configurer l'équilibrage de la charge réseau au niveau du matériel, consultez la documentation de votre fournisseur de matériel.  
  
### <a name="to-update-the-bam-configuration-to-reflect-the-location-of-the-cluster"></a>Pour mettre à jour la configuration de l'analyse BAM afin de prendre en compte l'emplacement du cluster  
  
1.  Utilisez l'utilitaire de gestion de l'analyse BAM pour obtenir la configuration BAM actuelle. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**et le type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm get-config-filename : myconfig.Xml.  
  
2.  Remplacez le nom de l'hôte local par celui du cluster d'équilibrage de charge réseau. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\myconfig.Xml.  
  
3.  Pour l'équilibrage de la charge réseau au niveau du matériel uniquement, vérifiez que le fichier de configuration est paramétré comme suit :  
  
    ```  
    <GlobalProperty Name="BAMVRoot">  
    http://<NLB IP Address>:portname/BAM</GlobalProperty>  
    ```  
  
    > [!NOTE]
    >  Les étapes 4 et 5 sont facultatives lors de la mise à jour de la configuration BAM avec l'équilibrage de la charge réseau au niveau du matériel.  
  
4.  Modifiez la ligne suivante pour la faire pointer vers le cluster d'équilibrage de charge réseau en remplaçant le nom de l'ordinateur (machinename) par celui du cluster :  
  
    ```  
    <GlobalProperty Name=" BAMVRoot">  http://machinename:portname/BAM  
    </GlobalProperty>   
    ```  
  
5.  Enregistrez la nouvelle configuration. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**et le type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm update-config-filename : myconfig.Xml.  
  
### <a name="to-edit-the-bam-portal-webconfig-file-to-change-the-bammanagementservice-and-queryservice-urls-to-point-to-the-nlb-server-name-note-this-procedure-is-not-necessary-for-hardware-based-nlb"></a>Pour modifier le fichier web.config du portail BAM afin que les URL de BAMmanagementService et de QueryService pointent vers le nom du serveur d'équilibrage de charge réseau. Remarque : Cette procédure n’est pas nécessaire pour l’équilibrage de charge basé sur le matériel réseau.  
  
1.  Ouvrez le fichier web.config à l’aide du bloc-notes en cliquant sur **Démarrer**, puis sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, puis en cliquant sur **OK**.  
  
2.  Modifiez le nom de l'ordinateur (machinename) et celui du port dans les deux lignes suivantes pour qu'ils pointent vers le nom du cluster :  
  
    ```  
    <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
    <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />   
    ```  
  
3.  Enregistrez le fichier. Pour ce faire, cliquez sur **fichier**, puis cliquez sur **enregistrer** dans la barre de menus du bloc-notes.  
  
### <a name="to-configure-each-additional-computer-in-the-cluster"></a>Pour configurer les ordinateurs supplémentaires dans le cluster  
  
1.  Copiez le fichier web.config dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal de chaque ordinateur du cluster.  
  
    > [!NOTE]
    >  Dans les étapes suivantes toutes les références à la **Program Files** sera **Program Files (x86)** pour les ordinateurs 64 bits.  
  
    > [!IMPORTANT]
    >  Dans les étapes suivantes, lorsque vous créez les répertoires virtuels, assurez-vous qu'ils possèdent les mêmes paramètres que les trois répertoires virtuels BAM créés par la configuration de BizTalk Server sur le premier ordinateur. Confirmez les chemins d'accès, la version ASP.NET, les autorisations sur les répertoires et le pool d'applications.  Pour exécuter BAMAppPool sur l'ordinateur que vous configurez, utilisez le même compte de service de domaine que celui utilisé lors de la configuration du premier ordinateur. Vérifiez que BAMAppPool est exécuté sur tous les ordinateurs. Vous devez copier deux fichiers web.config.  
    >   
    >  Outre le fichier web.config enregistré dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal, vous devez copier les fichiers web.config se trouvant dans les dossiers [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService et [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMQueryService dans les mêmes dossiers sur cet ordinateur.  
  
2.  Pour l'équilibrage de la charge réseau au niveau du matériel uniquement, modifiez le nom de l'ordinateur (machinename) et celui du port dans les deux lignes suivantes pour qu'ils pointent vers le nom du cluster :  
  
    ```  
    <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
    <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />  
    ```  
  
3.  Créer un pool d’applications appelé BAMAppPool.  
  
    > [!NOTE]
    >  Le chemin d’accès de répertoire pour les répertoires virtuels doit être % InstallationFolder%/BamPortal, % InstallationFolder%/BamPortal/BAMManagementService et % InstallationFolder%/BamPortal/BAMQueryService.  
  
4.  Créez un répertoire virtuel appelé BAM sous le site Web par défaut.  
  
5.  Remplacez le pool d'applications du répertoire virtuel BAM par le pool BAMAppPool.  
  
    > [!NOTE]
    >  Le chemin d'accès aux répertoires virtuels doit être le suivant : %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService et %InstallationFolder%/BamPortal/BAMQueryService.  
  
6.  Créez un répertoire virtuel appelé BAMManagementService sous BAM.  
  
7.  Remplacez le pool d'applications de BAMManagementService par le pool BAMAppPool.  
  
    > [!NOTE]
    >  Le chemin d’accès de répertoire pour les répertoires virtuels doit être % InstallationFolder%/BamPortal, % InstallationFolder%/BamPortal/BAMManagementService et % InstallationFolder%/BamPortal/BAMQueryService.  
  
8.  Créez un répertoire virtuel appelé BAMQueryService sous BAM.  
  
9. Remplacez le pool d'applications de BAMQueryService par le pool BAMAppPool.  
  
10. Pour modifier la version de l’analyse BAM, BAMMANAGEMENTSERVICE et BAMQUERYSERVICE définir la version des Applications pour .NET Framework 4, utilisez le INETMGR, situé sur l’onglet Propriétés ASP, du répertoire virtuel.  
  
11. Exécutez aspnet_setreg.exe -k:"SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\identity" -u:BAMWebServiceAccount -p:Password.  Le compte spécifié ici est le compte d'utilisateur de service Web de gestion BAM.  
  
    > [!CAUTION]
    >  Portail BAM *uniquement* s’exécute en mode 32 bits. Si IIS est installé sur un ordinateur 64 bits, ASP.NET 2.0 doit être activé en mode 32 bits. Pour ce faire, ouvrez le Gestionnaire des services Internet, ouvrez **Pool d’applications**, sélectionnez le pool d’applications (BAMAppPool), puis cliquez sur **paramètres avancés**. Dans **Activer les applications 32 bits**, sélectionnez **True**.  
    >   
    >  [Planification pour le portail BAM](../core/planning-for-the-bam-portal.md) répertorie les considérations supplémentaires.  
  
12. Définissez les listes de contrôle d'accès (ACL) en lecture pour les utilisateurs AppPool sur WebServices en exécutant SubInACL (outil de ligne de commande permettant aux administrateurs d'obtenir des informations de sécurité sur des fichiers), des clés de Registre et des services, et de transmettre ces informations d'un utilisateur à l'autre, d'un groupe local ou global à l'autre ou d'un domaine à l'autre.  
  
13. Télécharger l’outil SubInAcl à [http://go.microsoft.com/fwlink/?LinkId=61990](http://go.microsoft.com/fwlink/?LinkId=61990).  
  
14. Ouvrez une invite de commandes. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
15. Tapez la commande suivante à l’invite de commandes : subinacl.exe /subkeyreg « HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices » « / accorder = Service réseau = R »  
  
    > [!NOTE]
    >  L’objectif de cette commande doit accorder le Pool d’applications BAM utilisateur un accès en lecture à la clé de Registre SOFTWAREMicrosoftBizTalk Server3.0BAMWebServicesidentity. Cet exemple utilise le pool « Network Service » puisqu'il s'agit du pool utilisé par défaut par IIS. Si vous n'employez pas les paramètres IIS par défaut, vous devez vous servir de l'utilisateur du pool d'applications que votre déploiement utilise.  
  
16. Tapez la commande suivante à l’invite de commandes : subinacl.exe /keyreg « HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3. 0 » « / accorder =\<BAM WebService Account > »  
  
    > [!NOTE]
    >  L'objet de cette commande est d'accorder à l'utilisateur du service Web de gestion BAM un accès en lecture de la clé de Registre SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\Identity.  
  
17. Vérifiez que l'identité sous laquelle le pool d'applications BAM et le service Web de gestion BAM sont exécutés dispose d'un accès en lecture à la clé ASPNET_SETREG.  
  
18. Utilisez l'outil d'administration de la console Gestion de l'ordinateur pour ajouter l'utilisateur du service Web de gestion BAM et le compte de l'utilisateur du pool d'applications BAM au groupe Internet Information Services Worker Process (IIS_WPG) et au groupe SharePoint Services (STS_WPG).  
  
19. Définir les autorisations sur les dossiers temporaires ASP.NET pour le pool d’applications et les utilisateurs du service Web : c:\windows\system32\cacls « %windir%\Microsoft.NET\Framework\ v2.0. \<numéro de version > \Temporary ASP.NET Files » /T /E /G \<BAM WebService Account > : F  
  
    > [!NOTE]
    >  Vous devez accorder l'accès à la fois au compte d'utilisateur de service Web de gestion BAM et au compte d'utilisateur du pool d'applications BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion du portail BAM](../core/managing-the-bam-portal.md)