---
title: "Étape 5 : Promouvoir les propriétés de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, pomoted properties
- promoted properties
- schemas, promoted properties
ms.assetid: cb51cece-1b65-4ba2-b8e6-ce8b6694cdb6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d68ece5bedf7ec46a6d5ede7efc6878fa972fc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-5-promote-schema-properties"></a>Étape 5 : Promouvoir les propriétés de schéma
Dans cette étape, vous promouvez les propriétés de schéma afin qu’un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration peut faire référence à ces valeurs de propriété que vous créez dans les étapes ultérieures. La promotion est un mécanisme qui vous permet de faire référence à une valeur spécifique au sein d’une instance de message et le rendre accessible aux [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] composants tels que de l’orchestration ou pour le routage basé sur le contenu. En outre, une propriété promue est visible par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] IntelliSense dans l’éditeur d’Expression de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]l’audit et la fonctionnalité de journalisation avec l’outil de contrôle d’intégrité de BizTalk et l’activité de suivi du fonctionnement (HAT) peuvent suivre les propriétés de schéma promues uniquement.  
  
### <a name="to-promote-schema-properties"></a>Pour promouvoir des propriétés de schéma  
  
1.  Dans l’Explorateur de solutions, sous **BTAHL7 projet**, double-cliquez sur le **DoorBell.xsd** nœud pour ouvrir le schéma.  
  
2.  Cliquez sur le **FirstName** élément de champ, pointez sur **promouvoir**, puis cliquez sur **Promotion rapide**.  
  
3.  Cliquez sur **OK** pour ajouter le schéma de propriété au projet.  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Ajoute un cercle orange sur l’icône pour le **FirstName** élément, indiquant que l’élément a été promu.  
  
4.  Répétez ces étapes pour promouvoir les éléments de champ suivants :  
  
    -   **MiddleName**  
  
    -   **LastName**  
  
    -   **SSN**  
  
    > [!IMPORTANT]
    >  Il est important de noter que promouvoir un patient ID (PID) comme un numéro de sécurité sociale (SSN) provoque [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pour effectuer le suivi de cette propriété pour tous les messages entrants via le système. L’effet secondaire de cette situation est que la base de données de suivi des messages conserve une copie du patient numéros de sécurité sociale. Cela peut créer un problème de sécurité importantes. Vous devez protéger le magasin de données avec une extrême prudence ou éviter la promotion des données PID complètement.  
  
     Pour plus d’informations sur le suivi de documents basées sur les éléments de schéma que vous avez promues, consultez l’aide de BizTalk Server pour plus d’informations sur le suivi des activités et de contrôle d’intégrité.  
  
 Passez à [étape 6 : valider les schémas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’enrichissement des messages](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)