---
title: "Messages et champs clés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: 77db0706-dfdc-48b0-8ca4-bae7ab2d7641
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 524b5f361495d9509809a9229362d28a18712239
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="key-messages-and-fields"></a>Champs et les Messages de clé
Cette section décrit brièvement les messages et gérées par des champs clés le **OrderBroker** et **OrderManager** orchestrations. Pour obtenir une liste complète des messages dans l’application, consultez [référence de Message pour la Solution de gestion des processus métier](../core/message-reference-for-the-business-process-management-solution.md).  
  
## <a name="order-messages"></a>Messages de commande  
 Ordre des messages à partir de la **OrderBroker** sont des messages à parties multiples. L'une contient les informations de routage et l'autre, les informations de commande. La classe .NET définissant la partie consacrée au routage fait de tous ses champs des champs distinctifs, de façon à ce qu'une orchestration puisse avoir accès à tous les membres de classes en tant que propriétés de message. Les classes incluent également des champs promus dans la classe de routage afin que les messages puissent être acheminés. Tous les champs promus sont également des champs distinctifs afin qu'ils puissent être programmés et appelés avec une notation moins complexe.  
  
 Pour plus d’informations sur l’utilisation de classes .NET pour définir des messages, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
## <a name="identifying-orders"></a>Identification des commandes  
 La solution utilise trois champs dans les informations de routage pour identifier une commande. Parmi ces trois, deux identifient la commande : l’identificateur de commande (**OrderID**) et l’identificateur du client (**CustomerID**). Cependant, bien que ces deux champs identifient une commande, il peut y avoir plusieurs instances d'une commande. Par exemple, un client peut commander une nouvelle installation de câble standard puis changer sa commande en une nouvelle installation de câble de luxe. Il est peu probable que la commande d'origine soit terminée avant l'arrivée de la commande mise à jour. Cela crée deux instances de la commande.  
  
 Pour faire la distinction entre les instances de commandes, la solution utilise un numéro de séquence de commande unique (**SeqNum**). Les trois champs **OrderID**, **CustomerID**, et **SeqNum** identifier de façon unique une instance d’une commande.  
  
 Enfin, étant donné que la solution utilise des nombres croissants pour le **SeqNum**, la solution peut distinguer une mise à jour à partir de la commande d’origine, la mise à jour a un degré plus élevé **SeqNum**.  
  
> [!NOTE]
>  La solution s’appuie sur les systèmes de création de demandes de commande pour affecter des valeurs croissantes à **SeqNum**. Consultez le code-behind de la page ASP pour le service web d’entrée, **CSRMainForm.aspx.cs**et le mappage qui convertit la demande à une commande, **CSR_OrderRequest_To_Order.btm** pour les noms des champs impliqués.  
  
## <a name="status"></a>État  
 Le **OrderBroker**, **OrderManager**, et leurs orchestrations satellites utilisent deux champs dans la partie de routage de message de commande pour effectuer le suivi d’état : **état**et **Étape**. Le **état** champ effectue le suivi de l’état de la commande. Le tableau suivant décrit les valeurs pour le **état** champ.  
  
|Valeur|Où la valeur| Description|  
|-----------|---------------|-----------------|  
|ACCEPTED|OrderBroker|La commande peut être transmise à OrderManager.|  
|COMPLETED|OrderManager|Le traitement de l'ensemble de la commande est terminé sans erreur.|  
|ERROR|OrderManager|Une erreur a été détectée dans la commande.|  
|ORDERMANAGER-EXCEPTION|OrderManager|Une exception s'est produite dans le gestionnaire de commandes lors du traitement de la commande.|  
|STAGE_n_COMPLETED|OrderManager|Indique l'étape n, où n est un nombre, terminée sans erreur.|  
|STARTED|OrderManager|Le traitement de la commande a démarré.|  
|TERMINÉ|OrderManager|Le traitement de la commande est arrêté en raison d'une annulation.|  
  
## <a name="stage"></a>Étape  
 Le **OrderManager** utilise le **étape** champ dans la partie routage pour indiquer l’étape de traitement d’un message. Le champ est utilisé dans les filtres qui déterminent l'orchestration satellite qui traite le message. Le **OrderManager** définit initialement **étape** à un (1). Lorsque la commande est arrêtée ou terminée, le **OrderManager** définit **étape** à la valeur d’une variable d’orchestration, **arrêter**.  
  
## <a name="requesttype"></a>RequestType  
 Le **OrderManager** utilise également le **RequestType** champ du message de commande. Si la valeur du champ est TERMINATE, la commande doit être arrêtée. L’orchestration ignore toutes les autres valeurs de la **RequestType** champ et s’appuie sur les numéros de séquence de commande pour reconnaître les mises à jour et les doublons. Dans le cas contraire, le **OrderBroker** définit le **RequestType** au champ la valeur de la **état** champ dans le message à partir du système de service client ou fournisseur.  
  
## <a name="ordertypecode-ordertype-and-serviceclass"></a>OrderTypeCode, OrderType et ServiceClass  
 Le type de la commande est dans le **OrderTypeCode** champ du message de commande. Le **OrderBroker** lui affecte la valeur de la valeur de la **OrdTypeCode** champ dans le message en provenance de système de service client ou sur le système du fournisseur. Le tableau suivant montre les valeurs possibles pour **OrderTypeCode**:  
  
|Valeur| Description|  
|-----------|-----------------|  
|NS|Nouvelle installation de câble standard.|  
|ND|Nouvelle installation de câble de luxe.|  
|XS|Annuler l'installation de câble standard.|  
|XD|Annuler l'installation de câble de luxe.|  
|CS|Modifier l'installation de câble standard.|  
|CD|Modifier l'installation de câble de luxe.|  
|UNKNOWN|Inconnu.|  
  
 Une version ultérieure, le **Validate** orchestration utilise le moteur de règles d’entreprise pour convertir ces valeurs en deux champs distincts, **OrderType** et **ServiceClass**. Le **Validate** orchestration est appelée par le premier ordre de traitement, **CableOrder1**.  
  
 Le tableau suivant donne les valeurs pour le **OrderType**:  
  
|Valeurs OrderTypeCode|Valeur OrderType|  
|--------------------------|---------------------|  
|NS, ND|ACTIVATE|  
|XS, XD|CANCEL|  
|CS, CD|CHANGE|  
|Combinaison incorrecte.|INVALID|  
  
 Les valeurs de **ServiceClass** sont une lettre unique correspondante, **S** pour standard, ou **D** de luxe.  
  
## <a name="additional-identifiers"></a>Identificateurs supplémentaires  
 La solution utilise également un identificateur pour chaque commande individuelle. Cet identificateur, **RequestId**, doit être unique dans toutes les commandes. Le site Web d'entrée lui affecte automatiquement un GUID. Les messages envoyés par le biais de l'entrée par lot doivent inclure une valeur pour le champ. Le champ est **RequestID** dans le schéma de commande. Le **OrderBroker**, en revanche, utilise le **CSR_OrderRequest** schéma à traiter les commandes. Le champ apparaît sous la forme **ReqId** dans ce schéma et est une propriété unique.  
  
 La solution utilise le **RequestId** pour former l’identificateur d’activité utilisé dans le système de suivi BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)   
 [Flux de commandes par le biais du Gestionnaire de processus](../core/order-flow-through-the-process-manager.md)   
 [Construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md)   
 [Référence du message pour la Solution gestion des processus d’entreprise](../core/message-reference-for-the-business-process-management-solution.md)