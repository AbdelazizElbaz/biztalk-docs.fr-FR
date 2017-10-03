---
title: "Configuration des propriétés de l’enveloppe de secours (paramètres d’échange X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e9b05ea-2a0f-42d6-adc2-c1f1f2b7a993
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a2b0c43a43f5b003015378ecc52c05405877c5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-x12-interchange-settings"></a>Configuration des propriétés de l'enveloppe de secours (Paramètres d'échange X12)
Les paramètres de génération de l'enveloppe de l'échange X12 définissent la façon dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère l'enveloppe d'un échange X12 à envoyer au tiers récepteur. Dans cet accord de secours, vous définissez la méthode utilisée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour générer le segment ISA d'un échange X12 envoyé au tiers. Le segment ISA est l'en-tête de contrôle d'échange d'un échange X12.  
  
> [!NOTE]
>  Pour le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la longueur des champs ISA alphanumériques est fixe. Toutefois, pour le [!INCLUDE[TPM](../includes/tpm-md.md)] l’interface utilisateur, vous pouvez entrer un caractère unique pour un champ ISA alphanumérique. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]remplira ces champs avec les espaces de fin pour assurer la conformité avec les exigences.  
  
> [!NOTE]
>  Les paramètres décrits ici s'appliquent également à la génération de l'enveloppe de l'échange HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-define-the-envelope"></a>Pour définir l'enveloppe  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **enveloppes**.  
  
3.  Sous **d’ISA11**, conserver **identificateur Standard** sélectionné pour spécifier un identificateur standard au lieu d’un séparateur de répétition, puis sélectionnez une valeur pour l’identificateur standard dans la liste déroulante. Sélectionnez **séparateur de répétition** pour spécifier un séparateur de répétition au lieu d’un identificateur standard, puis entrez un caractère unique pour le séparateur de répétition. Le séparateur de répétition, qui permet de séparer les segments qui se répètent dans un document informatisé, est limité aux valeurs du jeu de caractères ASCII.  
  
4.  Pour **contrôler le numéro de version (ISA12)**, sélectionnez la version de la X12 standard à utiliser par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour générer un échange sortant.  
  
5.  Pour **l’indicateur d’utilisation (ISA15)**, sélectionnez cette option pour indiquer si un échange généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient des informations, les données de production, ou des données de test.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 propriétés d’accord de secours pour le traitement de l’échange](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)