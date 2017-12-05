---
title: Installer BizTalk Adapter Pack 2016 | Documents Microsoft
description: "Une installation standard ou personnalisée de 2016 BAP, éditions 32 bits et 64 bits, installez en mode silencieux"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f3e1717-8063-4460-bfdc-a933cd58a5c1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7076b9c076b263a54a436c553b519671760ca473
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-biztalk-adapter-pack-2016"></a>Installer BizTalk Adapter Pack 2016
Installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] des deux manières suivantes :  
  
-   **En mode interactif**: exécuter l’Assistant Installation  
  
-   **En mode silencieux**: utiliser la ligne de commande  
  
> [!IMPORTANT]
> - Vous devez disposer des privilèges d’administrateur sur l’ordinateur sur lequel vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], indépendamment de si vous installez à l’aide de l’Assistant, ou la ligne de commande.  
> - Être que toutes les le [les composants logiciels requis](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) sont installés avant d’installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].

## <a name="typical-vs-custom-installation"></a>Installation personnalisée d’installation par défaut et  
Répertorie les types d’installation, ainsi que les fonctionnalités qui sont installées avec chaque option :  
  
-   Le **standard** et **Complete** options installer toutes les cartes, avec les fournisseurs de données associé. Vous n’avez pas de l’option de choix d’une carte spécifique d’installation.  
  
-   Le **personnalisé** option installe une ou plusieurs cartes, avec les fournisseurs de données associé. Vous pouvez choisir les adaptateurs à installer. Si vous choisissez d’installer un fournisseur de données, vous devez également installer l’adaptateur correspondant. Toutefois, vous pouvez installer un adaptateur sans installer le fournisseur de données correspondant. Cela en développant le **ADO fournisseurs** nœud, puis en sélectionnant les fournisseurs que vous ne souhaitez pas installer. Consultez **installer à l’aide de l’Assistant Installation** (dans cette rubrique).  
  
     Par exemple, si vous installez le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], vous devez également installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]. Toutefois, vous pouvez installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] sans installer le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].  
  
## <a name="32-bit-and-64-bit-install-scenarios"></a>scénarios d’installation de 32 bits et 64 bits
 Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peut être utilisé pour : 
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]au moment du design (lors de la génération des métadonnées pour les opérations sur les applications métiers)
  
-   Moment du design console Administration de BizTalk Server (pour créer des ports physiques)
  
    > [!NOTE]
    >  Console d’Administration de BizTalk Server s’exécute comme une application de la Console MMC (Microsoft Management Console) 32 bits.  
  
-   Durée d’exécution BizTalk (pendant l’envoi et réception de messages à partir d’applications métier)

Vous pouvez utiliser un ordinateur unique pour toutes ces tâches, ou utiliser des ordinateurs distincts. Étant donné que les deux [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et MMC de BizTalk sont des processus 32 bits, vous devez installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sur l’ordinateur où vous effectuez les tâches de conception. 

### <a name="32-bit-install-scenario"></a>scénario d’installation 32 bits
Installer les logiciels suivants sur chaque ordinateur. Si vous utilisez un seul ordinateur, tous les logiciels doivent être installé sur cet ordinateur. 
 
1. Installer 32 bits[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]
2. Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].
3. Client d’installation 32 bits métier et d’autres requis DLL.  
  
### <a name="64-bit-install-scenarios"></a>scénarios d’installation 64 bits
  
|Pour le moment du design Visual Studio|Moment du design pour la console MMC de BizTalk|Pour le moment de l’exécution de BizTalk|Pour la conception de Visual Studio heure et/ou de conception BizTalk MMC + BizTalk moment de l’exécution|  
|---|---|---|---|  
|-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|**Pour un processus de BizTalk 32 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.<br /><br /> **Pour un processus BizTalk de 64 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer 64 bits LOB client et autres DLL requise.|**Pour un processus de BizTalk 32 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.<br /><br /> **Pour un processus BizTalk de 64 bits**:<br /><br /> -Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> -Installer 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer 64 bits LOB client et autres DLL requise.<br /><br /> -Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> -Installer le client LOB de 32 bits et d’autres DLL requise.|  
  
> [!NOTE]
>  Sur n’importe quel ordinateur où vous souhaitez effectuer des tâches de conception, à l’aide [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ou MMC de BizTalk, vous devez installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
## <a name="install-using-the-setup-wizard"></a>Installer à l’aide de l’Assistant Installation  
Étapes pour installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode interactif.  
  
1.  Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **setup.exe**.  
  
2.  Sélectionnez **installer des adaptateurs Microsoft BizTalk**. Dans la fenêtre suivante, un programme requis manquant est répertorié. Si un est manquant, puis sélectionnez le programme manquant et le programme d’installation l’installe pour vous. 

    Par exemple, sélectionnez **étape 2 : installer Microsoft BizTalk Adapter Pack** ou **étape 3 : installer Microsoft BizTalk Adapter Pack (x64)**.  
  
    > [!NOTE]
    >  Si vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sur un ordinateur virtuel, l’Assistant installation peut afficher un message qu’elle vérifie l’espace disque disponible. Si ce message apparaît se bloque ou restez, nous vous recommandons **installer en mode silencieux** (dans cette rubrique).  
  
3.  Dans l’écran de bienvenue, sélectionnez **suivant**.  
  
4.  Acceptez le contrat de licence utilisateur final (CLUF), puis sélectionnez **suivant**.  
  
5.  Dans **choisir le Type d’installation**:  
  
    -   Pour installer les fonctionnalités les plus courantes, sélectionnez **standard**.  
  
    -   Pour sélectionner les cartes que vous souhaitez installer, sélectionnez **personnalisé**, puis passez à l’étape suivante.  
  
    -   Pour installer toutes les fonctionnalités, sélectionnez **Complete**.  
  
        > [!IMPORTANT]
        >  Pour installer uniquement l’adaptateur que vous utilisez pour interagir avec votre application d’entreprise, sélectionnez le **personnalisé** installation.  
  
6. **Requis** uniquement si vous choisissez l’installation personnalisée. Si vous avez choisi le **standard** ou **Complete** installation, puis ignorez cette étape et passez à l’étape 7.  
  
    1.  Dans **installation personnalisée**, développez **Base adaptateurs** pour voir les adaptateurs disponibles.  
  
    2.  Pour les cartes que vous ne souhaitez pas, sélectionnez l’icône en regard de la carte, puis **totalité de cette fonctionnalité n’est pas disponible**.  
  
    3.  Développez **ADO fournisseurs**, puis sélectionnez les fournisseurs que vous ne souhaitez pas installer.  
  
    4.  Sélectionnez **Suivant**.  
  
7.  Sélectionnez **Installer**.  
  
8.  Dans **Customer Experience Improvement Program**, vous pouvez choisir de les inscrire. Si vous inscrivez, vous pouvez partager les données suivantes avec Microsoft :  
  
    -   Les données relatives au matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
    -   Les données relatives aux versions enterprise application vous utilisez avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
     [CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) fournit plus d’informations.  
     
     Sélectionnez **OK**. 
  
    > [!NOTE]
    >  Vous pouvez toujours modifier ce paramètre en exécutant le programme d’installation en mode de réparation à partir de **programmes**.  
  
9. Sélectionnez **Terminer**.  
  
<a name="BKMK_SilentInst"></a>   
## <a name="install-in-silent-mode"></a>Installer en mode silencieux  
 Utilisez le **msiexec** commande pour effectuer une installation sans assistance. Dans le cadre de la commande msiexec, entrez les composants individuels que vous souhaitez installer. Le tableau suivant répertorie les valeurs pour chaque composant dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Utilisez ces valeurs pour installer (ou supprimer) des composants spécifiques. Pour installer (ou supprimer) plusieurs composants, vous pouvez utiliser une combinaison de ces valeurs séparées par une virgule.  
  
|Nom du composant|Valeur correspondante pour les propriétés de ligne de commande|  
|---|---|  
|[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|DbFeature|  
|[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|OracleEBSFeature|  
|[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|SapBaseAdapterFeature|  
|[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|SiebelBaseAdapterFeature|  
|[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|SqlFeature|  
|[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|SapAdoFeature<br /><br /> **Remarque**: vous devez fournir cette valeur uniquement si vous installez le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] également.|  
|[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|SiebelAdoFeature<br /><br /> **Remarque**: vous devez fournir cette valeur uniquement si vous installez le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] également.|  
|Tous les composants|ALL|  
  
> [!IMPORTANT]
>  Les noms de fonctionnalités respectent la casse.  
  
 Les étapes suivantes vous montrent comment effectuer une installation silencieuse de [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour les différents composants.  
  
### <a name="silent-mode-steps"></a>Étapes de mode silencieux
  
1.  Ouvrez une invite de commandes et accédez à la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] racine dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.  
  
2.  Exécutez les commandes suivantes, selon ce que vous souhaitez installer :  
  
    > [!NOTE]
    >  Pour effectuer une installation sans assistance sur une plateforme x64 64, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi` dans les commandes suivantes.  
  
    -   Pour effectuer une installation complète, qui installe tous les adaptateurs, y compris les fournisseurs de données .NET Framework, tapez :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
        ```  
  
    -   Pour installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] avec [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
        ```  
  
    -   Pour installer le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
        ```  
  
    -   Pour installer uniquement le [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
        ```  
  
    -   Pour installer tous les adaptateurs de base, tapez :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
        ```  
  
    -   Pour installer les deux fournisseurs de données .NET Framework, tapez :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
        ```  
  
    -   N’importe quel type d’installation personnalisée en répartissant les composants par une virgule. Par exemple, pour installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] avec la [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]et le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
        ```  
  
    -   Vous pouvez également choisir d’inscrire pour CEIP dans le cadre de l’installation sans assistance. Type :  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
        ```  
  
         Par défaut, l’option est false. 
  
        > [!IMPORTANT]
        >  Lors de l’installation du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] version d’évaluation en mode silencieux, l’option par défaut pour CEIP est true.  
  
     Pour plus d’informations sur la **msiexec** de commandes, tapez `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`. Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).
     
## <a name="known-install-issue"></a>Problème d’installation connus
Pour une liste complète des problèmes d’installation, consultez **dépannage** rubriques pour chaque adaptateur.  
  
**Le programme d’installation en cours d’exécution sur un ordinateur 64 bits peut lever une erreur lors de l’accès au fichier de schéma**  
  
Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] le programme d’installation génère une erreur lors de l’accès à la Microsoft.Adapters. *\<AdapterName\>*_schema.xml fichier, mais se poursuit avec l’installation de l’adaptateur.  
  
**Cause**  
  
Si les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sont installés sur le même ordinateur, le fichier de schéma cible utilisé par les deux est la même. Par conséquent, le fichier est installé par 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peut être utilisé par IIS lorsque le programme d’installation 64 bits tente d’y accéder.  
  
**Résolution**  
  
Copiez manuellement le Microsoft.Adapters.  *\<AdapterName\>*fichier _schema.xml *C:\Program Files\Microsoft BizTalk Pack (x64) \IIS schémas* à *C:\Windows\System32\inetsrv\ config\schema*. 
  
## <a name="next-step"></a>Étape suivante
[Valider les étapes d’installation](../adapters-and-accelerators/post-installation-steps-for-biztalk-adapter-pack-2016.md)