---
title: "Annexe b : installer l’adaptateur SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f44c6e0a-dcce-4444-8cac-bd403c81a233
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0766eabdad71546090b703e41a00f496629d83
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="appendix-b-install-the-microsoft-sharepoint-adapter"></a>Annexe B : Installation de l’adaptateur Microsoft SharePoint
BizTalk Server inclut un adaptateur SharePoint qui peut recevoir des messages ou envoyer des messages à SharePoint. 

La configuration logicielle requise pour [BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) et [BizTalk Server 2013 R2 / 2013](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) répertorie les versions de SharePoint prises en charge.

## <a name="sharepoint-adapter-in-biztalk-server-2016"></a>Adaptateur SharePoint dans BizTalk Server 2016

Le programme d’installation de BizTalk Server installe automatiquement le package redistribuable CSOM, tout comme l’adaptateur de fichier, l’adaptateur FTP et les autres adaptateurs prêts à l’emploi. 

L’option SSOM a été supprimée et n’est pas disponible.


## <a name="sharepoint-adapter-in-biztalk-server-2013-and-r2"></a>Adaptateur SharePoint dans BizTalk Server 2013 et R2
Dans BizTalk Server 2013 R2 et BizTalk Server 2013, il existe deux options pour l’adaptateur SharePoint.

|Modèle objet SharePoint| Description|  
|-------------------------|-----------------|  
|CSOM - adaptateur SharePoint|**Recommandé**. Le programme d’installation de BizTalk Server installe automatiquement le package redistribuable CSOM, tout comme l’adaptateur de fichier, l’adaptateur FTP et les autres adaptateurs prêts à l’emploi. <br/><br/>Aucune configuration de l’installation n’est requise sur l’ordinateur SharePoint.|  
|SSOM - le Service Web de SharePoint|**Option déconseillée**. Sur l’ordinateur SharePoint, exécutez le programme d’installation de BizTalk Server, et **uniquement** sélectionner l’adaptateur SharePoint. Ce programme d’installation installe un service web IIS qui gère la communication avec l’adaptateur SharePoint sur le serveur BizTalk Server. <br/><br/>Dans la plupart des environnements, BizTalk Server et SharePoint sont sur des ordinateurs distincts.|  

##  <a name="BKMK_Before"></a> Avant l’installation  

*  Les composants SharePoint SSOM et CSOM peuvent être installés si BizTalk Server 2013 R2 ou 2013 et SharePoint sont installés sur le même ordinateur.  
  
* Le portail BAM n’est exécuté qu’en mode 32 bits. Si le portail BAM est installé sur un ordinateur 64 bits, vérifiez qu’ASP.NET 2.0 32 bits est activé et que le pool d’applications IIS utilise le mode 32 bits. Pour effectuer cette opération :  
  
    -   **ASP.NET** : Ouvrez le Gestionnaire des services Internet, cliquez sur le site web du **portail BAM**, puis double-cliquez sur **Mappages de gestionnaires**. Confirmez que **PageHandlerFactory-ISAPI-2.0** figure dans la liste **Activé**.  
  
    -   **Pool d’applications** : Ouvrez le Gestionnaire des services Internet, cliquez sur **Pools d’applications**, sur **BAMAppPool**, puis sur **Paramètres avancés**. Dans **Activer les applications 32 bits**, sélectionnez **True**.  
  
* Lors de l’installation de SharePoint, cliquez sur le **batterie de serveurs** option, même lorsque vous créez une installation monoserveur de BizTalk Server et SharePoint. A **batterie de serveurs** installation vous autorise à configurer les bases de données SharePoint.  
* [CSOM : L’adaptateur SharePoint Services](../core/csom-sharepoint-services-adapter.md) fournit des informations sur la configuration d’un emplacement de réception et d’un port d’envoi SharePoint.  
* BizTalk Server 2010 et les versions précédentes utilisent le modèle SSOM (Server Side Object Model) pour se connecter à SharePoint 2010. 

## <a name="csom-and-ssom-supported-versions"></a>Versions prenant en charge CSOM et SSOM  
Prise en charge SharePoint est répertorié dans le tableau suivant :  
  
||Prise en charge du modèle CSOM|Prise en charge du modèle SSOM|  
|---|---|---|  
|SharePoint 2016|Oui|non|  
|SharePoint 2013|Oui|non|  
|SharePoint Online|Oui|non|  
|SharePoint 2010|Oui|Oui|  
|SharePoint 2007 |non|Oui|  
  
##  <a name="BKMK_CSOM"></a> Installation de l’adaptateur SharePoint CSOM  
  
1.  Utilisez un ordinateur SharePoint avec la configuration suivante :  
  
    ||Prise en charge de CSOM|  
    |---|---|  
    |SharePoint 2016<br /><br /> [Installation de SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|Oui|  
    |SharePoint 2013<br /><br /> [Installation de SharePoint 2013](https://technet.microsoft.com/library/cc262957.aspx)|Oui|  
    |SharePoint Online<br /><br /> [Administration de SharePoint Online](https://technet.microsoft.com/library/gg132908.aspx)|Oui|  
    |SharePoint 2010<br /><br /> [Installation et déploiement pour SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Oui|  
    |SharePoint 2007 |non|  
  
2.  Sur le serveur BizTalk Server, installez Windows Identity Foundation :  
  
    | Système d'exploitation | Info |  
    |---|---|  
    |Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 et Windows Server 2012 R2|Windows Identity Foundation est inclus dans le système d’exploitation comme fonctionnalité dans **Activer ou désactiver des fonctionnalités Windows**.|  
    |Windows Vista SP1|Téléchargement disponible à la page [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331).|  
  
3.  Installation de BizTalk Server :

    | |  |  
    |---|---|  
     | BizTalk Server 2016 | Exécutez le programme d’installation de BizTalk. |
    | BizTalk Server 2013 R2 | Exécutez le programme d’installation de BizTalk et veillez à **ne pas** cocher **Adaptateur Windows SharePoint Services**. |  
    | BizTalk Server 2013 | Exécutez le programme d’installation de BizTalk et veillez à **ne pas** cocher **Adaptateur Windows SharePoint Services**. |
  
##  <a name="BKMK_SSOM"></a> Installation de l’adaptateur SharePoint SSOM (déconseillé)  
  
1.  Utilisez un ordinateur SharePoint avec la configuration suivante :  
  
    ||Prise en charge du modèle SSOM|  
    |---|---|  
    |SharePoint 2016<br /><br /> [Installation de SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|non| 
    |SharePoint 2013<br /><br /> [Installation de SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)|non|  
    |SharePoint Online<br /><br /> [Administration de SharePoint Online](https://technet.microsoft.com/library/gg132908.aspx)|non|  
    |SharePoint 2010<br /><br /> [Installation et déploiement pour SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Oui|  
    |SharePoint 2007<br /><br /> [Installation pour SharePoint Server 2007](https://technet.microsoft.com/library/cc262957(v=office.12).aspx) |Oui|  
  
2.  Sur l’ordinateur SharePoint, configurez SharePoint et étendre le Site Web par défaut. Lorsque vous étendez le site Web, un site Web IIS distinct est créé. Il inclut le même contenu, mais fournit également un type d’URL et d’authentification unique.  
  
     Consultez [SharePoint 2010 : Étendre une application Web](http://go.microsoft.com/fwlink/p/?LinkId=259124).  
  
3.  Sur l’ordinateur SharePoint, exécutez l’installation de BizTalk Server et **uniquement** vérifier **adaptateur Windows SharePoint Services**. Ceci permet d’installer le service Web. **N’exécutez pas la configuration de BizTalk**.  
  
4.  Sur le serveur BizTalk Server, installez BizTalk Server. Veillez à **ne pas** cocher **l’adaptateur Windows SharePoint Services**.  
  
5.  Le Service Web de SharePoint (SSOM) s’exécute uniquement en mode 64 bits. ASP.NET et le pool d’applications IIS doivent être configurés en mode 64 bits sur l’ordinateur SharePoint avant l’installation de SharePoint. Pour effectuer cette opération :  
  
    -   **ASP.NET** : Ouvrez le Gestionnaire des services Internet, cliquez sur le site web, puis double-cliquez sur **Mappages de gestionnaires**. Vérifiez que **PageHandlerFactory-ISAPI-2.0-64** figure dans la liste **Activé**.  
  
    -   **Pool d’applications** : Ouvrez le Gestionnaire des services Internet, cliquez sur **Pools d’applications**, sélectionnez le pool d’applications, puis cliquez sur **Paramètres avancés**. Dans **Activer les applications 32 bits**, sélectionnez **False**.  

