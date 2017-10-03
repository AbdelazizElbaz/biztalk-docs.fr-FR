---
title: Liaisons de port | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, warnings
- ports, bindings
- bindings, Web ports
- bindings, design time
- Web ports, port bindings
- bindings, ports
- bindings, direct
- bindings, warnings
- bindings, deployment
- bindings, dynamic
ms.assetid: b61c725a-0082-42d3-b88a-533583161734
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 943cbbaa6db9413ffad15bfcf3302d2216e3ab17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="port-bindings"></a>Liaisons de port
Une liaison de port représente les informations de configuration permettant de déterminer comment et où un message sera envoyé ou reçu. Selon son type, une liaison de port peut faire référence à des emplacements physiques, pipelines ou autres orchestrations.  
  
 Il existe trois types de liaison de port pour les ports de réception des messages :  
  
-   Spécifier maintenant  
  
-   Spécifier plus tard  
  
-   Direct  
  
 Il existe quatre types de liaison de port pour les ports d'envoi de message :  
  
-   Spécifier maintenant  
  
-   Spécifier plus tard  
  
-   Direct  
  
-   Dynamique  
  
## <a name="binding-at-deployment-time"></a>Liaison lors du déploiement  
 Vous pouvez lier votre port à un emplacement de réception ou à un port d'envoi. Si vous n’avez pas toutes les informations que vous devez spécifier un emplacement physique, vous pouvez sélectionner le **spécifier plus tard** option de liaison de port dans le Concepteur d’Orchestration et vous devez uniquement spécifier le type de port qui décrit le port. Une fois l'application déployée, vous pouvez indiquer les informations relatives à l'emplacement à l'aide de la console Administration de BizTalk Server ou d'un programme.  
  
## <a name="binding-at-design-time"></a>Liaison lors de la conception  
 Vous pouvez sélectionner le **spécifier maintenant** option de liaison dans le Concepteur d’Orchestration pour spécifier le transport et le pipeline au moment du design de port. Lorsque vous spécifiez le port de réception des messages, seuls les transports HTTP, SOAP et FILE sont disponibles dans la liste déroulante. Lorsque vous spécifiez le port d'envoi des messages, seuls les transports HTTP, FILE et SMTP sont disponibles dans la liste déroulante. Cette option est pratique si vous connaissez à l'avance la source ou la destination des messages transmis.  
  
## <a name="direct-binding"></a>Liaison directe  
 Les ports à liaison directe sont des ports logiques unidirectionnels ou bidirectionnels de vos orchestrations qui ne sont pas liés explicitement à des ports physiques. Ils vous permettent de disposer de différents modèles de communication dans vos services. Pour implémenter la liaison directe, sélectionnez le **Direct** option de liaison dans le Concepteur d’Orchestration au moment du design de port.  
  
 Il existe trois types de ports à liaison directe :  
  
-   Port à liaison directe MessageBox  
  
-   Port d'autocorrélation à liaison directe  
  
-   Port à liaison directe d'orchestration partenaire  
  
 Pour plus d’informations sur l’utilisation des ports à liaison directe, consultez [utilisation de Ports à liaison directe dans les Orchestrations](../core/working-with-direct-bound-ports-in-orchestrations.md).  
  
> [!NOTE]
>  Lorsque vous utilisez la liaison directe, vous ne pouvez pas échanger de messages entre un port requête-réponse et deux ports unidirectionnels.  
  
> [!NOTE]
>  La liaison directe n'est pas compatible avec les normes du Business Process Engineering Language for Web Services (BPEL4WS). Si vous requérez la conformité avec BPEL4WS, utilisez un autre type de liaison.  
  
## <a name="dynamic-binding"></a>Liaison dynamique  
 Dans les cas où la destination de la communication restera inconnue jusqu'à l'exécution, vous pouvez utiliser la liaison dynamique pour un port d'envoi. L’emplacement peut, par exemple, être déterminée à partir d’une propriété d’un message entrant et ensuite spécifié dans le **Expression** mettre en forme, comme indiqué dans le code suivant :  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
```  
  
 Pour plus d’informations sur la façon d’affecter dynamiquement des valeurs à des ports, consultez [comment affecter des valeurs à des Ports dynamiques](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md).  
  
## <a name="web-ports"></a>Ports Web  
 Si votre projet contient une référence à un service Web, le Concepteur d'orchestration la détectera et rendra disponible un type de port Web correspondant. Pour créer un port Web, ajoutez simplement un port à votre orchestration et affectez-lui un type de port Web existant. Pour plus d’informations, consultez [création de Ports Web](../core/creating-web-ports.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation des Types de ports](../core/how-to-work-with-port-types.md)   
 [Modèle de communication](../core/communication-pattern.md)   
 [Direction de communication](../core/communication-direction.md)   
 [L’utilisation de Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md)   
 [Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md)   
 [Utilisation de Services Web](../core/consuming-web-services.md)