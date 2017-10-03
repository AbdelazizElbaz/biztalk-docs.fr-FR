---
title: "Pour configurer Windows SharePoint Services emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, Windows SharePoint Services adapters
- configuring [Windows SharePoint Services adapters], receive locations
- Windows SharePoint Services adapters, receive locations
ms.assetid: 5db3d5cf-4a77-4985-bd03-307c520247ec
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22a23f97634eaba9dccccd099f7c39ba6af75d67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-windows-sharepoint-services-receive-location"></a>Configuration d'un emplacement de réception Windows SharePoint Services
Cette rubrique décrit la création et la configuration d'un emplacement de réception Windows SharePoint Services à l'aide de la console Administration de BizTalk Server.  
  
### <a name="to-create-and-configure-a-windows-sharepoint-services-receive-location"></a>Pour créer et configurer un emplacement de réception Windows SharePoint Services  
  
1.  Vérifiez que vous disposez d'un port de réception correctement configuré. Pour plus d’informations sur la façon de créer et configurer un port de réception, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
2.  Dans le **console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk [nom_groupe]**, développez  **Applications**, puis développez l’application que vous souhaitez créer un emplacement de réception.  
  
3.  Avec le bouton droit **emplacements de réception**, cliquez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
4.  Sélectionnez le port de réception qui contiendra cet emplacement de réception, puis cliquez sur **OK**.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue **Transport**, dans le **Type** zone de liste déroulante, sélectionnez **Windows SharePoint Services**.  
  
6.  Cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport Windows SharePoint Services** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Port de service Web d'adaptateur|Port HTTP du site Web IIS sur lequel est installé le service Web de l'adaptateur Windows SharePoint Services. Par défaut, il s’agit du Site Web par défaut configuré sur le port 80. Si vous avez configuré le service Web de Windows SharePoint Services sur n’importe quel autre que le Site Web par défaut du site Web IIS, vous devez mettre à jour cette valeur.|  
    |Délai d'expiration|Il s'agit du délai d'expiration, en millisecondes, des appels du service Web d'exécution de l'adaptateur adressés au service Web de l'adaptateur Windows SharePoint Services. Vous devrez éventuellement augmenter cette valeur si la taille du message ou du lot est supérieure à la valeur moyenne attendue par l'adaptateur.|  
    |Nom du fichier d'archive|(Facultatif) Nom de fichier Windows SharePoint Services du fichier archivé. Vous pouvez entrer une valeur littérale comme 'PurchaseOrder0001.xml' ou une expression. Les expressions peuvent se composer d'un mélange de littéraux, macros et requêtes XPATH, Par exemple, « PurchOrd-%XPATH=//po:PurchaseOrderId%-%MessageID%.xml ». Si aucun nom de fichier n'est fourni, le nom du fichier source est utilisé. Pour plus d’informations sur les expressions, consultez [Expressions de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md). **Remarque :** le « %sendingorchestrationid% » et « %sendingorchestrationtype% » macros ne sont pas pris en charge par ce champ.|  
    |URL d'emplacement d'archive|URL de dossier de Windows SharePoint Services, relative au site SharePoint, dans laquelle sont archivés les fichiers traités. Par exemple, Archive ou /Shared Documents/Processed Orders/. Si aucun emplacement d'archive n'est spécifié, le document est supprimé après traitement par l'adaptateur. **Remarque :** URL parfois la bibliothèque de documents SharePoint, ou un dossier est différent du nom de cet élément. Consultez la barre d'adresse d'Internet Explorer pour connaître l'URL correcte.|  
    |Remplacement archive|Détermine si les fichiers existants de l'archive sont remplacés. Sélectionnez « Oui » pour remplacer les fichiers existants. Sélectionnez « Non » pour que l'archivage échoue si un fichier du même nom existe déjà dans l'archive. Dans ce cas, le fichier reste extrait et doit être archivé manuellement. **Remarque :** lors de l’archivage des fichiers, nous vous recommandons d’utiliser les valeurs de nom du fichier d’Archive avec les macros afin de rendre le nom de fichier unique. À cette fin, vous pouvez utiliser un nom de fichier d'archive tel que PO-%MessageID%.xml ou PO-%XPATH=//ns0:PurchaseOrder/ns0:ID%.xml, où ID correspond à l'ID unique du bon de commande.|  
    |Taille de lot|Nombre maximal que le service Web de l'adaptateur de messagerie Windows SharePoint Services va traiter en un seul lot. Un lot traité peut contenir un nombre de messages inférieur à la taille du lot définie ; toutefois, il ne peut pas contenir un nombre de messages supérieur à cette taille.|  
    |Seuil d'erreur|Nombre maximal d'échecs d'interrogation consécutifs rencontrés par l'adaptateur avant que l'emplacement de réception ne soit désactivé. Définissez ce champ sur 0 afin de ne jamais désactiver l'emplacement de réception.|  
    |Alias d'espaces de noms|(Facultatif) Liste, séparée par des virgules ou des points-virgules, des définitions des alias d'espaces de noms. Ce champ permet de définir les alias d’espace de noms qui sont utilisés par les requêtes XPATH introduites dans le champ nom du fichier archives. Par exemple, po='http://OrderProcess/POrder', conf='http://OrderProcess/Confirmation' ipsol='{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'|  
    |Intervalle d’interrogation|Intervalle de temps, en secondes, entre deux requêtes consécutives exécutées par l'adaptateur pour vérifier si de nouveaux messages sont disponibles pour le traitement. **Remarque :** en spécifiant une valeur inférieure améliore le débit et temps de réponse pour l’adaptateur.|  
    |URL de site SharePoint|URL complète du site Web Windows SharePoint Services. Par exemple, http://BizTalkServer/sites/TestSite. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |URL bibliothèque documents source|URL de la bibliothèque de documents Windows SharePoint Services, relative au site SharePoint, où les documents sont extraits. Par exemple, /Shared Documents/ ou /New Purchase Orders/. **Remarque :** ne peut pas recevoir des messages à partir d’une liste SharePoint. Vous ne pouvez pas recevoir de messages d'un dossier SharePoint à moins d'utiliser une vue affichant les messages dans tous les dossiers. Pour ce faire, définissez la **dossiers** à une valeur de propriété **afficher tous les documents sans dossiers** lors de la création d’une vue. **Remarque :** la bibliothèque de documents SharePoint est parfois différente du nom de cet élément. Consultez la barre d'adresse d'Internet Explorer pour connaître l'URL correcte.|  
    |Nom de la vue|Vue Windows SharePoint Services utilisée pour filtrer les documents traités par l'adaptateur. Par exemple, Approved Orders. Laissez ce champ vide pour traiter tous les documents existants dans la bibliothèque de documents sources. Les dossiers affichés dans une vue et les messages contenus dans ces dossiers ne sont pas traités par l'adaptateur. Vous pouvez créer des affichages en 2D qui affichent dans une structure plate tous les documents y compris les documents présents dans les sous-dossiers. **Remarque :** tous les messages dans un affichage en 2D sont traités.|  
    |Intégration de Microsoft Office|« Facultatif » pour tenter de supprimer les instructions de traitement si possible ou, dans le cas contraire, traiter le document tel quel (par exemple, un document binaire). Choisissez « Oui » pour supprimer les instructions de traitement InfoPath ou ignorer le message en cas d'erreur. Choisissez « Non » pour traiter le document « tel quel ». Pour les messages binaires, vous devez utiliser les valeurs « Non » ou « Facultatif ».|  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer un gestionnaire d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [Comment configurer un Port d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)   
 [Référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Expressions de l’adaptateur de Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md)   
 [Prise en charge des Types de colonnes Windows SharePoint Services](../core/supported-windows-sharepoint-services-column-types.md)