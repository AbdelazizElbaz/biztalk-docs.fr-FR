---
title: "Valider les données d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c3ca83-0abf-42ba-8e29-653ff12d5e20
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86cde9d6133959e34ec09880be8a6beca5c37191
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validate-instance-data"></a>Valider les données d’Instance

## <a name="overview"></a>Vue d'ensemble
Au cours du processus de test d'un mappage, vous souhaiterez peut-être valider les données de l'instance par rapport aux schémas source et de destination afin de vérifier que les données de l'instance sont conformes à la structure des schémas. Pour valider un message d’instance par rapport au schéma source ou de destination, cliquez sur le schéma dans l’Explorateur de solutions, puis cliquez sur **valider l’Instance**.  
  
> [!IMPORTANT]
>  Si vous utilisez des données personnalisées ou des constantes dans votre sortie, vous devez vérifier que les types de vos données de test sources et les valeurs des constantes cibles sont valides. Quand vous validez un mappage, le Mappeur BizTalk ne vérifie pas si les données d'instance violent des types de données définis dans les schémas. Cette vérification a lieu lorsque vous testez le mappage ou que vous validez les données d'instance.  
  
 Pour plus d’informations sur comment générer et valider les données d’instance à l’aide de l’Éditeur BizTalk, consultez [génération d’un Message d’Instance et la Validation](../core/instance-message-generation-and-validation.md) et [Validation de l’Instance](../core/instance-validation.md). . Le **valeur** propriété du nœud d’un schéma affecte également la façon dont BizTalk génère des données d’instance. Pour plus d’informations, consultez la **propriétés de nœud de schéma** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
-  [Validation et génération de Message d’instance](../core/instance-message-generation-and-validation.md)   
-  [Comment valider des schémas dans Visual Studio](../core/how-to-validate-schemas-in-visual-studio.md)   
-  **Référence de la propriété de mappage**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
-  [Test de mappages](../core/testing-maps.md)