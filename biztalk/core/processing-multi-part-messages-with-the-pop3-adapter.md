---
title: "Parties multiples de traitement des Messages avec l’adaptateur POP3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ad041f-f155-4c1c-ab87-1405c80d9b68
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26aff4569414103ad8c4f37a9e4699a85874e481
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-multi-part-messages-with-the-pop3-adapter"></a>Traitement des messages à parties multiples avec l'adaptateur POP3
L’adaptateur POP3 peut traiter des messages au format MIME qui sont conformes aux normes IETF expliquées dans [RFC 2045](http://go.microsoft.com/fwlink/?LinkId=58810), [RFC 2046](http://go.microsoft.com/fwlink/?LinkId=58811), et [RFC 2047](http://go.microsoft.com/fwlink/?LinkId=58812). Les messages MIME peuvent être constitués d'une ou de plusieurs parties, avec différents types de contenus. Cette rubrique décrit la manière dont l'adaptateur POP3 traite les messages MIME à parties multiples.  
  
## <a name="receiving-multi-part-messages-with-the-pop3-adapter"></a>Réception de messages à parties multiples avec l'adaptateur POP3  
 Si un emplacement de réception qui utilise l’adaptateur POP3 a le **appliquer le décodage MIME** option définie sur **True** ensuite l’adaptateur POP3 effectue les actions suivantes lors de la réception d’un message codé au format MIME :  
  
1.  Crée un message BizTalk à parties multiples à partir des parties du message MIME reçu. Le message à parties multiples peut contenir d'une à plusieurs parties et contient le même nombre de parties que le message MIME reçu.  
  
2.  Analyse les en-têtes du message MIME. Si des en-têtes correspondent à la liste des propriétés décrites dans la rubrique [propriétés et schéma de propriété de l’adaptateur POP3](../core/pop3-adapter-property-schema-and-properties.md) ensuite ces en-têtes sont promues pour le message à parties multiples BizTalk en tant que propriétés de contexte.  
  
3.  Utilise un algorithme configurable pour désigner l'une des parties du message MIME en tant que corps du message BizTalk. L’algorithme utilisé pour déterminer la partie du message qui sera le corps du message BizTalk est décrit ci-dessous dans la section **corps partie sélection algorithme utilisé par l’adaptateur POP3**.  
  
4.  Publie le message BizTalk à parties multiples dans la base de données MessageBox.  
  
## <a name="body-part-selection-algorithm-used-by-the-pop3-adapter"></a>Algorithme de sélection du corps utilisé par l'adaptateur POP3  
 Lorsque l'adaptateur POP3 crée un message BizTalk à parties multiples à partir des parties du message MIME reçu, il sélectionne l'une des parties du message comme corps du message BizTalk. Le corps du message BizTalk est utilisé par BizTalk Server notamment pour la validation du message, le mappage, la promotion de propriétés, l'assembly de fichier plat et d'autres opérations. Les abonnés à un message BizTalk à parties multiples reçoivent toutes les parties du message mais n'utilisent que le corps désigné du message BizTalk, sauf utilisation d'une orchestration, d'un pipeline personnalisé ou d'un adaptateur qui peut comprendre les messages à parties multiples. Par exemple, vous pouvez configurer une orchestration pour lire toutes les parties d'un message à parties multiples. L'adaptateur SMTP peut lire toutes les parties d'un message à parties multiples et un pipeline personnalisé peut être configuré pour utiliser le composant de pipeline Encodeur MIME/SMIME. Pour plus d’informations sur l’utilisation d’une orchestration pour consommer un message à parties multiples, consultez la section ci-dessous, **traitement des Messages à parties multiples dans les Orchestrations**.  
  
 L’adaptateur POP3 sélectionne le corps du message BizTalk à partir des parties de corps disponibles en fonction des valeurs fournies pour le **Index du corps** et **Type de contenu du corps**.  
  
> [!NOTE]
>  L’adaptateur POP3 est conçu pour reconnaître les Types de contenu de partie de corps qui sont définies dans [RFC 2046](http://go.microsoft.com/fwlink/?LinkId=119569).  
  
 L'algorithme utilisé pour sélectionner le corps du message BizTalk d'un courrier électronique est décrit ci-après :  
  
1.  Si le **Index du corps** est définie sur 0 et **Type de contenu du corps** est vierge, l’algorithme suivant est utilisé pour sélectionner le corps du message BizTalk :  
  
    -   Utilisez la première partie MIME avec l'en-tête Content-Description défini sur « body ».  
  
    -   Sinon, utilisez la première partie MIME avec l'en-tête Content-Type défini sur « text/xml ».  
  
    -   Sinon, utilisez la première partie MIME avec l'en-tête Content-Type défini sur « text/plain ».  
  
    -   Sinon, utilisez la première partie MIME avec l'en-tête Content-Type défini sur « text/ ».  
  
    -   Sinon, utilisez la première partie MIME.  
  
2.  Sinon si le **Index du corps** est définie sur 0 et **Type de contenu du corps** est défini, alors que la première partie du corps du message entrant qui correspond à l’élément spécifié **Type du corps contenu** est sélectionné comme corps du message BizTalk. Si aucune partie ne correspond au type de contenu, le message est interrompu.  
  
3.  Sinon si le **Index du corps** est défini sur une valeur supérieure à 0 et la **Type de contenu du corps** est vide, puis dans le corps avec l’index spécifié est sélectionné comme corps du message BizTalk. Si l'index spécifié est supérieur au nombre de corps, le message est interrompu.  
  
4.  Sinon si le **Index du corps** est défini sur une valeur supérieure à 0 et la **Type de contenu du corps** est défini, le **Index du corps** ne s’applique qu’aux corps des composants qui correspondent à la chaîne **Type de contenu du corps** et le corps correspondant est sélectionné comme corps du message BizTalk. Si l'index spécifié est supérieur au nombre de corps avec un type de contenu correspondant, le message est interrompu. Si aucune partie ne correspond au type de contenu, le message est interrompu.  
  
5.  La partie sélectionnée comme corps du message BizTalk devient la première partie du message BizTalk à parties multiples publié dans la base de données MessageBox, tandis que les parties restantes du message gardent l'ordre qu'ils avaient dans le message MIME d'origine.  
  
## <a name="processing-multi-part-messages-in-orchestrations"></a>Traitement de messages à parties multiples dans des orchestrations  
 Lorsque l'adaptateur POP3 crée un message BizTalk à parties multiples à partir d'un message MIME reçu, toutes les parties sont publiées dans la base de données MessageBox même si une seule partie est désignée comme corps du message BizTalk. Ces parties peuvent être ensuite utilisées par une orchestration abonnée au message à parties multiples. Cette section décrit certaines considérations lors du traitement de messages à parties multiples dans une orchestration.  
  
### <a name="processing-multi-part-messages-with-a-known-number-of-parts-and-known-part-types"></a>Traitement de messages à parties multiples avec un nombre connu de parties et des types de parties connus  
 Si votre orchestration reçoit un message à parties multiples avec un nombre connu de parties et des types de parties connus, vous pouvez déclarer un message à parties multiples dans l'orchestration et définir le nombre de parties et les types de parties au moment de la conception.  
  
### <a name="processing-multi-part-messages-with-unknown-part-types"></a>Traitement de messages à parties multiples avec des types de parties inconnus  
 Si votre orchestration reçoit un message à parties multiples avec des types de parties inconnus, vous pouvez déclarer un message à parties multiples dans l’orchestration et utiliser le **XmlDocument** type pour chacune des parties pour laquelle le type est inconnu.  
  
### <a name="processing-multi-part-messages-with-an-unknown-number-of-parts-and-all-of-the-part-types-are-unknown"></a>Traitement de messages à parties multiples avec un nombre inconnu de parties et tous les types de parties inconnus  
 Si votre orchestration reçoit un message à parties multiples avec un nombre inconnu de parties, que vous pouvez déclarer un message à parties multiples avec une seule partie de la **XmlDocument** type dans l’orchestration pour recevoir le message. Si un message à parties multiples contenant supérieur au nombre de parties déclarés est reçu, les lectures du moteur d’orchestration combien dénombre les parties contenues dans le message, construit ensuite les types de parties propres pour les parties qui correspondant au nombre de parties du message déclaré type et constructions **XmlDocument** parties pour les parties restantes.