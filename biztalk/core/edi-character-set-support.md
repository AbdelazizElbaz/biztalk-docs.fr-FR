---
title: "Prise en charge du jeu de caractères EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4f4492b-8cbe-48ed-810a-3e73e1cb5996
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c1463d8a06ab5da89306aababfe19362d6308dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-character-set-support"></a>Prise en charge du jeu de caractères EDI
Cette rubrique présente les jeux de caractères pris en charge dans les fonctionnalités EDI de [!INCLUDE[prague](../includes/prague-md.md)].  
  
|Codage EDI|Jeux de caractères pris en charge|  
|------------------|------------------------------|  
|X12 (y compris HIPAA)|X12 - Jeu de caractères de base (sous-ensemble d'ASCII)|  
|-|X12 - Jeu de caractères étendu (sous-ensemble d'ASCII, inclut également des caractères ISO8859-1)|  
|-|UTF8/UNICODE|  
|EDIFACT|UNOA|  
|-|UNOB|  
|-|UNOC - ISO 8859-1 : traitement des informations - partie 1 : alphabet Latin n° 1|  
|-|KECA - KS_C_5601-1987 (page de codes 949 Windows)|  
|-|UNOX (ISO2022 – JP)|  
|-|De données codées UNOY - UTF8 **Remarque :** les caractères UNOD à UNOK définit qui prennent en charge UTF-8 données encodées sont également pris en charge.|  
  
## <a name="setting-the-edi-character-set"></a>Configuration du jeu de caractères EDI  
 Dans un échange X12, vous pouvez définir le jeu de caractères d'un pipeline en configurant la propriété de pipeline CharacterSet. Pour plus d’informations, consultez [configuration des propriétés de Pipeline EDI](../core/configuring-edi-pipeline-properties.md).  
  
> [!NOTE]
>  Il existe un contrôle du jeu de caractères X12 dans la page Génération de l'enveloppe d'échange X12 de la boîte de dialogue Propriétés X12/EDI de la console Administration de BizTalk Server, mais celui-ci sert uniquement à valider les valeurs des propriétés entrées dans la boîte de dialogue Propriétés EDI.  
  
 Pour les échanges EDIFACT, vous avez la possibilité de définir le jeu de caractères pour un tiers en configurant la propriété de tiers UNB1.1 sur Tiers en tant que récepteur d'échanges dans la page de propriétés Définition du segment UNB. Le codage utilisé dans un échange entrant est déterminé par la valeur du champ UNB1.1 de l'en-tête de l'échange. Pour plus d’informations, consultez [configuration des enveloppes (EDIFACT-paramètres des documents informatisés)](../core/configuring-envelopes-edifact-transaction-set-settings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de Pipeline EDI](../core/configuring-edi-pipeline-properties.md)   
 [Configuration d’enveloppes (EDIFACT-informatisés paramètres)](../core/configuring-envelopes-edifact-transaction-set-settings.md)