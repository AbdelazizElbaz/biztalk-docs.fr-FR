---
title: "Activation de la réception de plusieurs échanges dans un seul Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98bcd2e-495a-49d8-a471-6e23b1e161f9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec1b282908424100ddfd0363fd6bede9011d53a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-the-receiving-of-multiple-interchanges-in-a-single-message"></a>Activation de la réception de plusieurs échanges dans un seul message
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut traiter un message contenant plusieurs échanges. Un tel message X12 inclurait plusieurs en-têtes ISA et codes de fin IEA. Un tel message EDIFACT inclurait quant à lui plusieurs en-têtes UNA/UNB et codes de fin UNZ.  
  
 Pour activer le désassembleur EDI dans le pipeline EdiReceive ou AS2EdiReceive d’analyser plusieurs échanges dans un seul message, vous devez définir le **DetectMID** propriété de pipeline **True**. (MID signifie Multiple Interchange Disassembling [Désassemblage de plusieurs échanges]). Par défaut, cette propriété est définie sur True.  
  
 Lorsque le pipeline de réception qui inclut le Désassembleur EDI reçoit un message contenant plusieurs échanges, le Désassembleur analyse chaque échange depuis son en-tête jusqu'à son code de fin. Ce traitement est effectué selon les règles suivantes :  
  
-   Tous les échanges d'un même message doivent posséder le même type de codage, à savoir soit X12 soit EDIFACT. Si ce n'est pas le cas, le Désassembleur EDI traite tous les échanges disposant du même type de codage que celui du premier échange du message. Il ignore les échanges possédant un type de codage différent de celui du premier échange.  
  
-   Le Désassembleur EDI ignore tout caractère situé entre le code de fin d'un échange et l'en-tête de l'échange suivant.  
  
-   Si vous activez l’authentification en sélectionnant le **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue** propriété du port de réception, puis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sera suspendre le message entier si l’un des échanges dans le message échoue.  
  
-   Si vous activez l'authentification et si l'un des échanges du même message ne correspond à aucun accord, tous les échanges du message sont interrompus et aucun accusé de réception n'est renvoyé, même pour les échanges correspondant à un accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-enable-the-receiving-of-multiple-interchanges-in-a-message"></a>Pour activer la réception de plusieurs échanges dans un message  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **emplacements de réception** nœud, avec le bouton de l’emplacement de réception que vous souhaitez activer la réception de plusieurs échanges au sein d’un seul message, puis cliquez sur  **Propriétés**.  
  
2.  Cliquez sur les points de suspension en regard du pipeline de réception (à savoir soit EdiReceive soit AS2EdiReceive).  
  
3.  Dans le **configurer le Pipeline** boîte de dialogue, définissez la **DetectMID** propriété de pipeline **True**.  
  
4.  Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution EDI](../core/configuring-ports-for-an-edi-solution.md)