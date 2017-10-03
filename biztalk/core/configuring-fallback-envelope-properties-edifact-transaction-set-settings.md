---
title: "Configuration des propriétés de l’enveloppe de secours (EDIFACT-informatisés paramètres) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b56a5a93-35ac-4293-b00e-28dcd89dfa2a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c93f9aae6d67e5dc56d383626e36d1db412be9d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-edifact-transaction-set-settings"></a>Configuration des propriétés d'enveloppe de secours (EDIFACT pour les paramètres des documents informatisés)
Dans le **enveloppes** page de la **paramètres des documents informatisés** section, vous définissez la façon dont BizTalk Server génère les segments UNG pour un échange EDIFACT envoyé au tiers.  
  
 Le segment UNG est l'en-tête qui identifie et indique un groupe fonctionnel d'un échange EDIFACT. Il contient la date et l'heure de préparation du groupe fonctionnel, ainsi que le type et la version du document inclus dans le groupe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-define-the-ung-segments"></a>Pour définir les segments UNG  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres des documents informatisés** , cliquez sur **enveloppes** .  
  
3.  Pour **ID de groupe fonctionnel (UNG1)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de six caractères. Ce champ est obligatoire.  
  
4.  Entrez des valeurs pour identifier les **expéditeur de l’Application (UNG2)**.  
  
    -   Pour **d’Identification (UNG2.1)**, entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum. Ce champ est obligatoire.  
  
    -   Pour **qualificateur de Code (UNG2.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de quatre caractères. Il s’agit d’un champ facultatif.  
  
5.  Entrez des valeurs pour identifier les **destinataire de l’Application (UNG3)**.  
  
    -   Pour **d’Identification (UNG3.1)**, entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum. Ce champ est obligatoire.  
  
    -   Pour **qualificateur de Code (UNG3.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de quatre caractères. Il s’agit d’un champ facultatif.  
  
6.  Pour **agence de contrôle (UNG6)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de deux caractères. Ce champ est obligatoire.  
  
7.  Entrez des valeurs pour identifier les **version du Message (UNG7)**.  
  
    -   Pour **Version (UNG7.1)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de trois caractères. Ce champ est obligatoire.  
  
    -   Pour **version finale (UNG7.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de trois caractères. Ce champ est obligatoire.  
  
    -   Pour **d’Association assigné (UNG7.3) de code**, entrez une valeur alphanumérique contenant au minimum 1 caractère et un maximum de 6 caractères. Il s’agit d’un champ facultatif.  
  
8.  Pour **passe d’Application (UNG8)**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères. Ce champ est obligatoire.  
  
9. Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés d’accord de secours EDIFACT Transaction définie les paramètres](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)