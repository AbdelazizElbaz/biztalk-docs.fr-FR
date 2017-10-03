---
title: "Installation d’AppFabric Connect pour les Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1de3bf49-e3cc-4d3f-9883-9a2c472f3647
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3d10862a6a60d173cc68c25d0dcc463d2f16e38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-appfabric-connect-for-services"></a>Installation d’AppFabric Connect pour les Services
Ce guide fournit des instructions sur l’installation de BizTalk Server 2010 Feature Pack (octobre 2010). Le pack de fonctionnalités installe BizTalk Server 2010 AppFabric Connect de fonctionnalité de Services qui fournit des améliorations apportées à la **Assistant Publication du Service WCF BizTalk** et **WCF Assistant développement d’adaptateurs**. Après avoir installé le pack de fonctionnalités, vous serez en mesure d’étendre la portée de votre site sur les artefacts de BizTalk Server ou LOB applications dans le nuage en ajoutant un point de terminaison du Bus des services Windows Azure AppFabric.  
  
## <a name="prerequisites"></a>Conditions préalables  
 BizTalk Server 2010 Feature Pack apporte des améliorations à l’Assistant de publication des services WCF BizTalk et l’Assistant développement d’adaptateurs WCF. L’Assistant de publication des services WCF BizTalk est disponible avec les outils de développement BizTalk Server 2010, Assistant développement d’adaptateurs WCF est disponible avec le Pack adaptateurs BizTalk 2010. Par conséquent, avant d’installer le feature pack, vous devez disposer des outils de développement BizTalk Server 2010 ou Pack adaptateurs BizTalk 2010 ou les deux installés. Si vous en avez qu’un seul de ces installé, l’Assistant pertinents pour l’installation du produit parent sera mis à jour dans le cadre de l’installation de pack de fonctionnalités.  
  
 Sinon, il existe certaines conditions requises pour l’utilisation de ces Assistants. La liste complète des conditions préalables requises pour chaque Assistant est répertoriée dans les rubriques qui expliquent comment utiliser les Assistants. Les liens vers les rubriques sont fournis sous [à l’aide de AppFabric Connect pour les Services](../technical-guides/installing-appfabric-connect-for-services.md#BKMK_Using).  
  
## <a name="installing-biztalk-server-2010-feature-pack"></a>L’installation de BizTalk Server 2010 Feature Pack  
 Procédez comme suit pour installer AppFabric Connect pour les Services :  
  
#### <a name="to-install-the-feature-pack"></a>Pour installer le feature pack  
  
1.  Télécharger le AppFabric Connect pour les Services qui peut être installés à partir de [http://go.microsoft.com/fwlink/?LinkId=204701](http://go.microsoft.com/fwlink/?LinkId=204701). Exécutez le fichier à extraction automatique BizTalkServer2010_FeaturePack.exe pour lancer le programme d’installation du pack de fonctionnalités.  
  
2.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
3.  Acceptez les termes du contrat de licence, puis **suivant** puis, dans l’écran suivant, cliquez sur **suivant** à nouveau.  
  
4.  Une fois l’Assistant termine l’installation de pack de fonctionnalités, cliquez sur **Terminer**.  
  
##  <a name="BKMK_Using"></a>L’utilisation de AppFabric de se connecter pour les Services  
 Après l’installation d’AppFabric Connect pour les Services, vous pouvez effectuer les éléments suivants :  
  
-   Utilisez le **Assistant Publication du Service WCF BizTalk** pour exposer les artefacts BizTalk (orchestration, schéma, etc.) en tant que services WCF avec un point de terminaison de relais sur Azure AppFabric Service Bus. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=204700](http://go.microsoft.com/fwlink/?LinkId=204700).  
  
-   Utilisez le **Assistant développement d’adaptateurs WCF** d’exposer des opérations sur les applications métier en tant que services WCF avec un point de terminaison de relais sur Azure AppFabric Service Bus. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=204699](http://go.microsoft.com/fwlink/?LinkId=204699).  
  
## <a name="uninstalling-biztalk-server-2010-feature-pack"></a>Désinstallation de BizTalk Server 2010 Feature Pack  
 Cette section fournit des instructions sur la désinstallation AppFabric Connect pour les Services.  
  
#### <a name="to-uninstall-the-feature-pack"></a>Pour désinstaller le pack de fonctionnalités  
  
1.  Ouvrez Windows Update, cliquez sur **afficher l’historique de mise à jour**, puis cliquez sur **mises à jour installées**.  
  
2.  Dans la liste des mises à jour installées, sous **BizTalk Server 2010** catégorie, avec le bouton droit **BizTalk Server 2010 Feature Pack (octobre 2010) LDR**, puis sélectionnez **désinstallation**. Dans la boîte de dialogue Confirmer si vous souhaitez désinstaller le pack de fonctionnalités, cliquez sur **Oui**.  
  
3.  Actualiser la liste pour vérifier si le feature pack est désinstallé.  
  
## <a name="copyright"></a>copyright  
 Ce document concerne une version préliminaire d'un logiciel qui pourrait subir des modifications importantes avant son lancement commercial officiel.  Ce document est fourni à titre d'information uniquement et Microsoft exclut toute garantie, expresse ou implicite, en ce qui concerne ce document.  Les informations contenues dans ce document, y compris les adresses URL et les autres références à des sites Internet, pourront faire l'objet de modifications sans préavis.  Le risque lié à l'utilisation ou aux résultats d'utilisation de ce document incombe entièrement à l'utilisateur.  Sauf mention contraire, les sociétés, organisations, produits, noms de domaine, adresses de messagerie, logos, personnes, lieux et événements mentionnés dans les exemples sont fictifs.  Toute ressemblance avec des sociétés, organisations, produits, noms de domaine, adresses de messagerie, logos, personnes, lieux ou événements réels est purement fortuite et involontaire.  L’utilisateur est tenu d’observer la réglementation relative aux droits d’auteur applicable dans son pays.  Aucune partie de ce document ne peut être reproduite, stockée ou introduite dans un système de restitution, ou transmise à quelque fin ou par quelque moyen que ce soit (électronique, mécanique, photocopie, enregistrement ou autre) sans la permission expresse et écrite de Microsoft Corporation.  
  
 Les produits mentionnés dans ce document peuvent faire l'objet de brevets, de dépôts de brevets en cours, de marques, de droits d'auteur ou d'autres droits de propriété intellectuelle et industrielle de Microsoft.  Sauf stipulation expresse contraire d'un contrat de licence écrit de Microsoft, la fourniture de ce document n'a pas pour effet de vous concéder une licence sur ces brevets, marques, droits d'auteur ou autres droits de propriété intellectuelle.  
  
 © 2010 Microsoft Corporation.  Tous droits réservés.  
  
 Microsoft, Active Directory, ActiveX, BizTalk, Excel, InfoPath, JScript, IntelliSense, Internet Explorer, MSDN, Outlook, PivotChart, PivotTable, PowerPoint, SharePoint, Tahoma, Visio, Visual Basic, Visual C++, Visual C#, Visual SourceSafe, Visual Studio, Win32, Windows, Windows NT, Windows PowerShell, Windows Server, Windows Server System, et Windows Server sont des marques déposées du groupe Microsoft.  
  
 SAP, R/3, mySAP, mySAP.com, xApps, xApp, SAP NetWeaver et les autres produits et services SAP mentionnés ici, ainsi que leurs logos respectifs, sont soit des marques de SAP, soit des marques déposées de SAP en Allemagne et dans d'autres pays. Tous les autres noms de produit et de service mentionnés sont des marques de leurs propriétaires respectifs. Les données dans ce document sont fournies à titre indicatif uniquement. Les spécifications nationales relatives aux produits peuvent varier.  
  
 Toutes les autres marques sont la propriété de leurs propriétaires respectifs.