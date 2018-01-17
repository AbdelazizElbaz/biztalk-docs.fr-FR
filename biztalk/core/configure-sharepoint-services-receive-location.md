---
title: "Configurer SharePoint Services emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9afed0e4-0f72-4df4-a2cb-d999c6fbbc86
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 807f13611b7e8977e0d5067787717427efc4bed2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="configure-sharepoint-services-receive-location"></a>Configuration d’un emplacement de réception SharePoint Services
Cette rubrique énumère les étapes nécessaires à la création d’un emplacement de réception [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)].  
  
## <a name="create-a-receive-location"></a>Créer un emplacement de réception  
 Lors de la création d’un emplacement de réception, celui-ci utilise le Gestionnaire de réception par défaut associé au Type de transport. Lorsque vous utilisez la [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] carte, la valeur par défaut est de gestionnaire de réception **BizTalkServerApplication**. Pour savoir comment ajouter un nouveau gestionnaire de réception, accédez à [comment créer un gestionnaire d’adaptateur](http://go.microsoft.com/fwlink/p/?LinkId=263646).  
  
 Créer l’emplacement de réception :  
  
1.  Dans le **Administration de BizTalk Server** de la console, développez **groupe BizTalk [*GroupName*]**, développez **Applications**, puis développez l’application à contenir l’emplacement de réception.  
  
2.  Créer un **unidirectionnel Port de réception**. [Comment créer un Port de réception](../core/how-to-create-a-receive-port.md) répertorie les étapes.  
  
    > [!IMPORTANT]
    >  A **demander un emplacement de réception réponse** n’est pas configurable avec les [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] carte.  
  
     Les options de configuration supplémentaires du port de réception comprennent notamment :  
  
     [Comment ajouter un emplacement de réception à un Port de réception](../core/how-to-add-a-receive-location-to-a-receive-port.md): un emplacement de réception est ajouté à l’étape suivante.  
  
     [Comment configurer les mappages entrants pour un Port de réception](../core/how-to-configure-inbound-maps-for-a-receive-port.md)  
  
     [Comment configurer le suivi d’un Port de réception](../core/how-to-configure-tracking-for-a-receive-port.md)  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
4.  Avec le bouton droit **emplacements de réception**, cliquez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
    > [!IMPORTANT]
    >  A **demander un emplacement de réception réponse** n’est pas configurable avec les [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] carte.  
  
5.  Sélectionnez le port de réception, puis cliquez **OK**.  
  
6.  Dans **propriétés**, entrez la **nom** et **pipeline** propriétés. Dans le **Type** la liste déroulante, cliquez sur **Windows SharePoint Services** et sélectionnez le **Gestionnaire de réception** propriété.  
  
7.  Cliquez sur **configurer**. Dans **propriétés**, configurez les éléments suivants :  
  
    |||  
    |-|-|  
    |Port de service Web d'adaptateur|**Requise**. Il s'agit du port configuré sur le site Web IIS hébergeant le service Web de l'adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].<br /><br /> Port par défaut est **80**, qui est le port HTTP standard. Si vous utilisez un autre port, vous devez mettre à jour cette valeur.|  
    |Délai d'expiration|**Requise**. Cette valeur, exprimée en millisecondes, détermine le délai d'attente pour que l'adaptateur reçoive une réponse du service Web.<br /><br /> Valeur par défaut est **100 000 ms** (100 secondes).<br /><br /> Augmentez cette valeur si la taille du message ou du lot est supérieure à celle prévue.|  
    |Utiliser le modèle objet client|**Requise**. Détermine si le modèle CSOM (Client-side Server Object Model) ou le modèle SSOM (Service-Side Object Model) SharePoint est utilisé.<br /><br /> Valeur par défaut est **Oui**. La valeur **Oui** à utiliser le CSOM SharePoint sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il n’existe aucune configuration requise sur l'ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].<br /><br /> La valeur **non** à utilisent le SSOM SharePoint qui inclut le service web installé sur le [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ordinateur.<br /><br /> [Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations spécifiques sur les composants SSOM et CSOM utilisés par les [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] carte.|  
    |Nom du fichier d'archive|**Facultatif**. Les services Web [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] peuvent archiver des documents à partir d’une bibliothèque SharePoint. Entrez le nom du fichier archivé.<br /><br /> Entrez un nom de fichier, tel que **PurchaseOrder0001.xml** ou une expression. Les expressions incluent toute combinaison de littéraux, de macros et de requêtes XPATH. Par exemple, « PurchOrd-%XPATH=//po:PurchaseOrderId%-%MessageID%.xml ». Si aucun nom de fichier n’est fourni, le nom de fichier du fichier source est utilisé. Consultez [Expressions de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md) pour plus d’informations. **Remarque :** le « %sendingorchestrationid% » et « %sendingorchestrationtype% » macros ne sont pas pris en charge par ce champ.|  
    |URL d'emplacement d'archive|**Facultatif**. URL du dossier [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] pour stocker les documents archivés. Entrez le chemin d'accès relatif au site SharePoint, Par exemple, **Archive** ou **Shared Documents/Processed Orders /**. Si un emplacement d’archive n’est pas indiqué, le document est supprimé après avoir été traité par l’adaptateur. **Remarque :** l’URL de bibliothèque ou un dossier de documents SharePoint peut être différent de son nom. Consultez l'adresse dans le navigateur Web pour connaître l'URL exacte.|  
    |Remplacement archive|**Requise**. Indiquez qu’il faut remplacer les fichiers existants.<br /><br /> Valeur par défaut est **non**, ce qui fait échouer l’archive si un fichier portant le même nom existe dans l’archive. Dans ce scénario, le fichier est vérifié et doit être manuellement archivé. **Remarque :** lorsque les fichiers d’archivage, utilisez des valeurs de nom du fichier archives avec les macros le nom de fichier est unique. Par exemple, utilisez un nom de fichier d’Archive tel que **PO-%MessageID%.xml or PO-%XPATH=//ns0:PurchaseOrder/ns0 :*ID*%.xml**, où ID est l’ID de commande fournisseur unique.|  
    |Taille de lot|**Requise**. Nombre maximal de documents traités par le service Web par lot. Un lot traité peut contenir moins de messages que la taille de lot définie. Il ne contient plus de messages.<br /><br /> Valeur par défaut est **20** et doit avoir au moins la valeur **1**.|  
    |Seuil d'erreur|**Requise**. Nombre maximal d’échecs d’interrogation consécutifs rencontrés par l’adaptateur avant que l’emplacement de réception ne soit désactivé.<br /><br /> Valeur par défaut est **10**. Pour arrêter l’emplacement de réception d’être désactivé, affectez la valeur **0**.|  
    |Alias d'espaces de noms|**Facultatif**. Il s'agit d'une liste, séparée par des virgules ou des points-virgules, des définitions d'alias d'espaces de noms.<br /><br /> Ce champ vous permet de définir les alias d’espaces de noms utilisés par les requêtes XPATH introduites dans le champ Nom de fichiers d’archive listées ci-dessus. Par exemple, entrez **po = 'http://OrderProcess/POrder', conf = 'http://OrderProcess/Confirmation' ipsol = '{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'**.|  
    |Intervalle d’interrogation|**Requise**. Temps écoulé, en secondes, entre deux requêtes consécutives exécutées par l’adaptateur qui attend de nouveaux messages.<br /><br /> Valeur par défaut est **60** et doit avoir au moins la valeur **1**. **Remarque :** pour améliorer la carte de débit et temps de réponse, entrez une valeur inférieure.|  
    |URL de site SharePoint|**Facultatif**. Il s'agit de l'URL complète du site Web [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], Par exemple, http:// *SharePointServer*  /sites/TestSite. **Remarque :** un port d’envoi ou emplacement de réception URI ne peut pas dépasser 256 caractères.|  
    |URL bibliothèque documents source|**Facultatif**. Chemin d’accès relatif de la bibliothèque de documents [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] où les documents sont récupérés, Par exemple, **/Shared Documents /** ou **/New Purchase Orders /**. **Remarque :** la bibliothèque de documents SharePoint peut être différente de son nom. Consultez l'adresse dans le navigateur Web pour connaître l'URL exacte.|  
    |Nom de la vue|**Facultatif**. le [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] vue utilisée pour filtrer les documents traités par l’adaptateur. Par exemple, **Approved Orders**.<br /><br /> Pour traiter tous les documents existants dans la bibliothèque de documents source, laissez ce champ vide. Les dossiers d’une vue et les messages de ces dossiers ne sont pas traités par l’adaptateur. Créer des affichages en 2D qui affichent dans une structure plate tous les documents, y compris les documents présents dans les sous-dossiers.|  
    |Intégration de Microsoft Office|**Requise**. Pour les messages binaires, vous devez utiliser les valeurs « Non » ou « Facultatif ».<br /><br /> Valeur par défaut est **facultatif**.<br /><br /> Les options sont les suivantes :<br /><br /> -   **Ne**: traite le document « tel quel ». Vous pouvez utiliser cette option pour les messages binaires.<br />-   **Facultatif**: essaie de supprimer les instructions de traitement InfoPath. Si les instructions de traitement ne sont pas supprimées, le document est traité « tel quel ». Vous pouvez utiliser cette option pour les messages binaires.<br />-   **Oui**: instructions de traitement InfoPath de supprime. Si une erreur se produit, le message est ignoré.|  
    |Mot de passe SharePoint Online|**Facultatif**. Il s'agit du mot de passe associé au compte SharePoint Online.|  
    |Nom d'utilisateur SharePoint Online|**Facultatif**. Il s'agit du nom d'utilisateur associé au compte SharePoint Online.|  
  
8.  Cliquez sur **OK** enregistrer les paramètres.  
  
9. Les options de configuration supplémentaires de l’emplacement de réception comprennent notamment :  
  
     [Comment configurer la planification pour un emplacement de réception](../core/how-to-configure-scheduling-for-a-receive-location.md)  
  
10. Cliquez sur **OK** enregistrer les paramètres.  
  
 Rubriques supplémentaires sur le port et l’emplacement de réception :  
  
 [Gestion des ports de réception](../core/managing-receive-ports.md)  
  
 [Gestion des emplacements de réception](../core/managing-receive-locations.md)  
  
 Ensuite, créez un port d’envoi [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] :  
  
 [Configurer un port d’envoi SharePoint Services](../core/configure-sharepoint-services-send-port.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le Port d’envoi SharePoint Services](../core/configure-sharepoint-services-send-port.md)   
 [Résolution des problèmes de l’adaptateur SharePoint Services](../core/troubleshooting-sharepoint-services-adapter.md)   
 [Modèle CSOM : Adaptateur SharePoint Services](../core/csom-sharepoint-services-adapter.md)