---
title: "Configuration des propriétés de l’enveloppe de secours (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a951f70-07d5-4a58-b1ea-e7117a45c545
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7aa7898d1e1a83da879400a89d5cd089ef2d4069
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-x12-transaction-set-settings"></a>Configuration des propriétés d'enveloppe de secours (X12 pour les paramètres des documents informatisés)
Dans le **enveloppes** page de la **paramètres des documents informatisés** section, vous définissez la façon dont BizTalk Server génère les segments GS pour un échange codé X12 qu’elle envoie au tiers. Un segment GS identifie et spécifie un groupe fonctionnel pour un échange X12.  
  
> [!NOTE]
>  Cette rubrique s'applique également aux paramètres liés à HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-define-the-gs-segments"></a>Pour définir les segments GS  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres des documents informatisés** , cliquez sur **enveloppes**.  
  
3.  Pour **code fonctionnel (GS01)**, sélectionnez une valeur dans la liste déroulante.  
  
4.  Pour **Application émettrice (GS02)**, entrez une valeur alphanumérique contenant au minimum de 2 et un maximum de 15. Ce champ est obligatoire.  
  
5.  Pour **Application réceptrice (GS03)**, entrez une valeur alphanumérique contenant au minimum de 2 et un maximum de 15. Ce champ est obligatoire.  
  
6.  Pour **format de Date (GS04)**, sélectionnez SSAAMMJJ ou aammjj dans la liste déroulante. Ce champ est obligatoire.  
  
7.  Pour **format d’heure (GS05)**, sélectionnez HHMM, HHMMSS ou Hhmmssjj dans la liste déroulante. Ce champ est obligatoire.  
  
8.  Pour **entité responsable (GS07)**, sélectionnez la valeur dans la liste déroulante.  
  
9. Pour **identificateur de Document (GS08)**, entrez une valeur alphanumérique comportant un minimum de 1 et un maximum de 12. Il s’agit d’un champ facultatif.  
  
10. Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 définir les propriétés de l’accord de secours pour la Transaction paramètres](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)