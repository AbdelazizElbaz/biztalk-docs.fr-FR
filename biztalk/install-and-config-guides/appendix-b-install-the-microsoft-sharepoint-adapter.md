---
title: "Annexe b : installer l’adaptateur Microsoft SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f44c6e0a-dcce-4444-8cac-bd403c81a233
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f67c888d844182daa6ecdc8e65e13487b8b337f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-b-install-the-microsoft-sharepoint-adapter"></a>Annexe B : Installation de l’adaptateur Microsoft SharePoint
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] pouvant échanger des messages avec [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]. 

Cette rubrique décrit l’adaptateur SharePoint.  La configuration logicielle requise pour [BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) et [BizTalk Server 2013 R2 / 2013](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) répertorie les versions de SharePoint prises en charge.

## <a name="sharepoint-adapter-in-biztalk-server-2016"></a>Adaptateur SharePoint dans BizTalk Server 2016

Le programme d’installation de BizTalk Server installe automatiquement le package redistribuable CSOM, tout comme l’adaptateur de fichier, l’adaptateur FTP et les autres adaptateurs prêts à l’emploi. 

L’option SSOM a été supprimée et n’est pas disponible.


## <a name="sharepoint-adapter-in-biztalk-server-2013-and-r2"></a>Adaptateur SharePoint dans BizTalk Server 2013 et R2
Dans [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013, il existe deux options pour l’adaptateur SharePoint.

|Modèle objet SharePoint|Description|  
|-------------------------|-----------------|  
|Adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] - CSOM|**Recommandé**. Le programme d’installation de BizTalk Server installe automatiquement le package redistribuable CSOM, tout comme l’adaptateur de fichier, l’adaptateur FTP et les autres adaptateurs prêts à l’emploi. <br/><br/>Aucune configuration de l’installation n’est requise sur l’ordinateur SharePoint.|  
|Service Web [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]- SSOM|**Déconseillé**. Sur l’ordinateur SharePoint, exécutez le programme d’installation de BizTalk Server, et sélectionnez **uniquement** l’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]. Ce programme d’installation installe un service web IIS qui gère la communication avec l’adaptateur SharePoint sur le serveur BizTalk Server. <br/><br/>Dans la plupart des environnements, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] sont installés sur des ordinateurs distincts.|  

##  <a name="BKMK_Before"></a> Avant l’installation  

*  Les composants SSOM et CSOM de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] peuvent tous deux être installés si [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] ou 2013 et [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] sont installés sur le même ordinateur.  
  
* Le portail BAM n’est exécuté qu’en mode 32 bits. Si le portail BAM est installé sur un ordinateur 64 bits, vérifiez qu’ASP.NET 2.0 32 bits est activé et que le pool d’applications IIS utilise le mode 32 bits. Pour effectuer cette opération :  
  
    -   **ASP.NET** : Ouvrez le Gestionnaire des services Internet, cliquez sur le site web du **portail BAM**, puis double-cliquez sur **Mappages de gestionnaires**. Confirmez que **PageHandlerFactory-ISAPI-2.0** figure dans la liste **Activé**.  
  
    -   **Pool d’applications** : Ouvrez le Gestionnaire des services Internet, cliquez sur **Pools d’applications**, sur **BAMAppPool**, puis sur **Paramètres avancés**. Dans **Activer les applications 32 bits**, sélectionnez **True**.  
  
* Lors de l’installation de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], cliquez sur l’option **Batterie de serveurs**, même lorsque vous créez une installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] à un seul serveur. Une installation de type **batterie de serveurs** vous permet de configurer les bases de données [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].  
* [CSOM : L’adaptateur SharePoint Services](../core/csom-sharepoint-services-adapter.md) fournit des informations sur la configuration d’un emplacement de réception et d’un port d’envoi SharePoint.  
* BizTalk Server 2010 et les versions précédentes utilisent le modèle SSOM (Server Side Object Model) pour se connecter à SharePoint 2010. 

## <a name="csom-and-ssom-supported-versions"></a>Versions prenant en charge CSOM et SSOM  
La prise en charge de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] est indiquée dans le tableau suivant :  
  
||Prise en charge du modèle CSOM|Prise en charge du modèle SSOM|  
|-|-------------------|-------------------|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2016|Oui|Non|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2013|Oui|Non|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Online|Oui|Non|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2010|Oui|Oui|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2007 |Non|Oui|  
  
##  <a name="BKMK_CSOM"></a> Installation de l’adaptateur SharePoint CSOM  
  
1.  Utilisez un ordinateur SharePoint avec la configuration suivante :  
  
    ||Prise en charge de CSOM|  
    |-|------------------|  
        |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2016<br /><br /> [Installation de SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|Oui|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2013<br /><br /> [Installation de SharePoint 2013](https://technet.microsoft.com/library/cc262957.aspx)|Oui|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Online<br /><br /> [Administration de SharePoint Online](https://technet.microsoft.com/library/gg132908.aspx)|Oui|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2010<br /><br /> [Installation et déploiement pour SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Oui|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2007 |Non|  
  
2.  Sur le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], installez Windows Identity Foundation :  
  
    | Système d'exploitation | Info |  
    |-|-|  
    |[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 10, [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 8.1, [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Server 2016, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] et [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2|Windows Identity Foundation est inclus dans le système d’exploitation comme fonctionnalité dans **Activer ou désactiver des fonctionnalités Windows**.|  
    |[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] SP1|Téléchargement disponible à la page [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331).|  
  
3.  Installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :

    | |  |  
    |-|-|  
     | [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] | Exécutez le programme d’installation de BizTalk. |
    | [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] | Exécutez le programme d’installation de BizTalk et veillez à **ne pas** cocher **Adaptateur Windows SharePoint Services**. |  
    | BizTalk Server 2013 | Exécutez le programme d’installation de BizTalk et veillez à **ne pas** cocher **Adaptateur Windows SharePoint Services**. |
  
##  <a name="BKMK_SSOM"></a> Installation de l’adaptateur SharePoint SSOM (déconseillé)  
  
1.  Utilisez un ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] avec la configuration suivante :  
  
    ||Prise en charge du modèle SSOM|  
    |-|------------------|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2016<br /><br /> [Installation de SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|Non| 
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2013<br /><br /> [Installation de SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)|Non|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Online<br /><br /> [Administration de SharePoint Online](https://technet.microsoft.com/library/gg132908.aspx)|Non|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2010<br /><br /> [Installation et déploiement pour SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Oui|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2007<br /><br /> [Installation pour SharePoint Server 2007](https://technet.microsoft.com/library/cc262957(v=office.12).aspx) |Oui|  
  
2.  Sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], configurez SharePoint et étendez le site web par défaut. Lorsque vous étendez le site Web, un site Web IIS distinct est créé. Il inclut le même contenu, mais fournit également un type d’URL et d’authentification unique.  
  
     Consultez [SharePoint 2010 : Étendre une application Web](http://go.microsoft.com/fwlink/p/?LinkId=259124).  
  
3.  Sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], exécutez l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et cochez **uniquement** l’**adaptateur Windows SharePoint Services**. Ceci permet d’installer le service Web. **N’exécutez pas la configuration de BizTalk**.  
  
4.  Sur le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Veillez à **ne pas** cocher **l’adaptateur Windows SharePoint Services**.  
  
5.  Le service Web [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (SSOM) n’est exécuté qu’en mode 64 bits. ASP.NET et le pool d’applications IIS doivent être configurés en mode 64 bits sur l’ordinateur SharePoint avant l’installation de SharePoint. Pour effectuer cette opération :  
  
    -   **ASP.NET** : Ouvrez le Gestionnaire des services Internet, cliquez sur le site web, puis double-cliquez sur **Mappages de gestionnaires**. Vérifiez que **PageHandlerFactory-ISAPI-2.0-64** figure dans la liste **Activé**.  
  
    -   **Pool d’applications** : Ouvrez le Gestionnaire des services Internet, cliquez sur **Pools d’applications**, sélectionnez le pool d’applications, puis cliquez sur **Paramètres avancés**. Dans **Activer les applications 32 bits**, sélectionnez **False**.  

