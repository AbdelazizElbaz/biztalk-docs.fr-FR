---
title: "Traitement des messages de façons d’utiliser le contenu du Message au contrôle de code | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1e3792e-9cd4-42b6-8b9d-3c2a022a16d6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73d356496d07bb2227aa514ee68f2a2a51e2291b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-use-message-content-to-control-message-processing"></a>Utilisations du contenu de message pour contrôler le traitement de message
Il existe deux types de promotions de propriétés : **champs distinctifs** et **champs de propriété**, le deuxième utilise les schémas de propriété. Dans l’Éditeur BizTalk, vous gérez ces deux types de promotions de propriétés à l’aide de la **promouvoir les propriétés** boîte de dialogue, qui est accessible à l’aide de la **promouvoir les propriétés** propriété de la  **Schéma** nœud.  
  
> [!NOTE]
>  Il existe certaines restrictions concernant les valeurs qu'il est possible de promouvoir. Pour plus d’informations, consultez le tableau dans [promotion des propriétés](../core/promoting-properties.md).  
  
 En fonction des détails de votre scénario, vous devez décider du type de promotion de propriétés à utiliser. Observez les distinctions entre **champ distinctif** promotion de propriétés et **champ de propriété** promotion de propriétés :  
  
-   **Champs distinctifs** ne peut pas participer au routage des messages et par conséquent, ils n’apparaissent pas dans les expressions de filtre. Ils sont uniquement disponibles dans le contexte d'une orchestration, mais nécessitent moins de traitement lors de l'envoi et de la réception de messages.  
  
-   **Champs distinctifs** n’ont pas de limitation de taille. **Champs de propriété** sont limités à 255 caractères.  
  
-   **Champs distinctifs** ne nécessitent pas d’artefacts distincts tandis que de créer **champs de propriété** nécessitent la création et la maintenance d’un schéma de propriété.  
  
 Grâce à ces considérations, vous devez promouvoir des nœuds en tant que **champs de propriété** uniquement lorsque vous envisagez d’utiliser les propriétés promues pour le routage du message ou à des fins de suivi. Sinon, si vous vous apprêtez uniquement pour accéder aux propriétés promues à partir de vos orchestrations, vous devez tirer parti du fait que **champs distinctifs** sont bien plus économique, plus légers et plus facile à utiliser que  **Champs de propriété**.  
  
 Propriétés promues à l’aide de la **champ distinctif** mécanisme sont uniquement accessible à partir d’orchestrations et ne sont pas accessibles à partir des pipelines, les ports et ainsi de suite. En revanche, les propriétés promues à l’aide de la **champs de propriété** et le mécanisme de schéma de propriété sont accessibles à partir de tous ces composants. Une autre différence importante réside dans le fait que les valeurs de champ de propriété sont limitées à 255 caractères et que les valeurs de champ distinctif ne font pas l'objet d'une telle limite.  
  
 Cette section fournit des informations sur ces deux types de promotions de propriétés et notamment sur la manière d'établir de telles propriétés promues pour un schéma de message en utilisant l'Éditeur BizTalk.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [À propos des propriétés de contexte de Message BizTalk](../core/about-biztalk-message-context-properties.md)  
  
-   [Le traitement des messages d’instance à l’aide des champs distinctifs](../core/instance-message-processing-using-distinguished-fields.md)  
  
-   [Traitement de Message d’instance à l’aide de la Promotion de propriétés](../core/instance-message-processing-using-property-promotion.md)