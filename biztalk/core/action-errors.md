---
title: "Erreurs d’action | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cf0a5b-d1dd-4807-9660-e8a8b7012b40
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f25f1f15307077943ef370a335885690bea22c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="action-errors"></a>Erreurs en relation avec les actions
Cette section inclut des informations détaillées sur le diagnostic et la résolution des erreurs en relation avec les actions WCF.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Une action unique ne peut pas contenir de caractères de nouvelle ligne. Supprimez tous les caractères de nouvelle ligne ou, pour spécifier plusieurs actions, utilisez la syntaxe du mappage d'actions.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que la propriété d'action d'un port d'envoi inclut un caractère de nouvelle ligne, ce qui n'est pas autorisé.  
  
> [!NOTE]
>  Cette restriction ne s'applique pas lorsque l'action est définie en tant que mappage.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de résoudre la propriété d'action.  
  
 
1.  Ouvrez **Administration de BizTalk Server.**  
  
2.  Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.  
  
3.  Localisez votre application, puis votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Sélectionnez **propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Sélectionnez **Configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, sélectionnez le **général** onglet.  
  
9. Dans le **en-tête d’Action SOAP** section, supprimez le caractère de nouvelle ligne à partir de la **Action** zone de texte.  

## <a name="more-good-info"></a>Plus d’informations correct  
 Pour plus d’informations sur les actions, consultez [spécifiant les Actions SOAP pour envoyer les adaptateurs WCF](../core/specifying-soap-actions-for-wcf-send-adapters.md)