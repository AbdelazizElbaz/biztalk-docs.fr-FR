---
title: "Assemblage : définition d’une Solution de gestion des partenaires commerciaux | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4219312a-c4b5-45f3-b77b-d5cc4f1a1ca4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea32fba8e9e57d7a0549a680b06e08d5bf8e087f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="putting-it-all-together-defining-a-trading-partner-management-solution"></a>Définition d'une solution de gestion des partenaires commerciaux
Maintenant que nous connaissons les différents types de composants constitutifs d'une solution GPC (Gestion des partenaires commerciaux), considérons le flux d'une solution GPC classique et la manière dont les blocs de construction fonctionnent ensemble. Cette section répertorie également quelques méthodes conseillées pour modéliser une solution GPC.  
  
 Un flux classique permettant de créer une solution GPC inclut les éléments suivants :  
  
1.  Création de partenaires représentant les organisations impliquées dans un échange commercial. Par exemple, si deux organisations commerciales sont impliquées dans un échange, vous devez alors créer un partenaire commercial pour chacune d'entre elles. Pour obtenir des instructions sur la création des partenaires commerciaux, consultez [configuration des propriétés de tiers générales](../core/configuring-general-party-properties.md) ou [configuration des propriétés de tiers générales (AS2)](../core/configuring-general-party-properties-as2.md)  
  
2.  Pour chaque département d'une organisation, créez un profil dans le partenaire représentant le département. Par exemple, si une organisation possède les départements « Achat » et « Fournitures », chacun de ces départements doit être représenté en tant que profil d'entreprise dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous devez non seulement créer les profils d'entreprise pour le partenaire représentant votre organisation, mais aussi pour le partenaire avec lequel vous échangez. Pour obtenir des instructions sur la création de profils d’entreprise, consultez [configuration des propriétés de profil d’entreprise](../core/configuring-business-profile-properties.md).  
  
3.  Pour chaque profil d'entreprise, définissez les paramètres du protocole B2B, à savoir le paramètre de codage des messages et les paramètres de protocole des messages. Ces paramètres définissent la manière dont les messages B2B sont codés et acheminés d'un profil d'entreprise à un autre.  
  
    > [!NOTE]
    >  À cette étape, la spécification des paramètres de protocole est facultative. Vous pouvez ajouter ces paramètres directement dans l'accord de partenariat commercial.  
  
4.  Création d'accords de partenariat commercial (TPA) entre les profils d'entreprise pour définir le codage et/ou les protocoles de messagerie auxquels ils seront soumis lors de l'échange de messages. Pour obtenir des instructions sur la façon de créer des accords, voir [configuration des propriétés d’accord spécifique X12](../core/configuring-x12-specific-agreement-properties.md), [propriétés configuration de l’accord EDIFACT spécifiques](../core/configuring-edifact-specific-agreement-properties.md), ou [AS2 de configuration Propriétés de l’accord](../core/configuring-as2-agreement-properties.md).  
  
 En ayant réalisé l'ensemble des tâches décrites ci-dessus, vous devriez avoir créé une solution GPC permettant d'échanger des messages B2B avec votre partenaire commercial.  
  
## <a name="where-do-i-start"></a>Où commencer ?  
 Vous pouvez commencer par parcourir les sections suivantes :  
  
-   Didacticiel spécifique X12 [didacticiel 2 : EDI Interface Developer Tutorial](../core/tutorial-2-edi-interface-developer-tutorial.md).  
  
-   Didacticiel AS2 spécifique [didacticiel 3 : didacticiel AS2](../core/tutorial-3-as2-tutorial.md).  
  
-   X12-et EDIFACT-procédures pas à pas spécifiques sous [de développement et de configuration des Solutions EDI de BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md).  
  
-   Procédures pas à pas de AS2 spécifiques sous [de développement et de configuration des Solutions AS2 de BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md).  
  
-   Créer des parties, les profils et accords pour X12 et EDIFACT en suivant les instructions à la messagerie [configuration des propriétés EDI](../core/configuring-edi-properties.md).  
  
-   Créer des parties, les profils et accords pour AS2 en suivant les instructions à la messagerie [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md)