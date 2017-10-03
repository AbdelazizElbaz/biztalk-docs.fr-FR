---
title: "Configuration d’enveloppes (paramètres d’échange X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4fade73-14cf-475c-81b5-6102c75db991
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf4f88ee1e5d786367c1a4bc0f5b2404fd5c1a37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-x12-interchange-settings"></a>Configuration d'enveloppes (paramètres d'échange X12)
Les paramètres de génération de l'enveloppe de l'échange X12 définissent la façon dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère l'enveloppe d'un échange X12 à envoyer au tiers récepteur. Dans cette section, vous définissez la méthode utilisée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour générer le segment ISA d'un échange X12 envoyé au tiers. Le segment ISA est l'en-tête de contrôle d'échange d'un échange X12.  
  
> [!NOTE]
>  Pour le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la longueur des champs ISA alphanumériques est fixe. Toutefois, pour le [!INCLUDE[TPM](../includes/tpm-md.md)] l’interface utilisateur, vous pouvez entrer un caractère unique pour un champ ISA alphanumérique. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]remplira ces champs avec les espaces de fin pour assurer la conformité avec les exigences.  
  
> [!NOTE]
>  Les paramètres décrits ici s'appliquent également à la génération de l'enveloppe de l'échange HIPAA.  
  
> [!IMPORTANT]
>  Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-define-the-envelope"></a>Pour définir l'enveloppe  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **enveloppes**.  
  
3.  Sous **d’ISA11**, conserver **identificateur Standard** sélectionné pour spécifier un identificateur standard au lieu d’un séparateur de répétition, puis sélectionnez une valeur pour l’identificateur standard dans la liste déroulante. Sélectionnez **séparateur de répétition** pour spécifier un séparateur de répétition au lieu d’un identificateur standard, puis entrez un caractère unique pour le séparateur de répétition. Le séparateur de répétition, qui permet de séparer les segments qui se répètent dans un document informatisé, est limité aux valeurs du jeu de caractères ASCII.  
  
4.  Pour **contrôler le numéro de version (ISA12)**, sélectionnez la version de la X12 standard à utiliser par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour générer un échange sortant.  
  
5.  Pour **l’indicateur d’utilisation (ISA15)**, sélectionnez cette option pour indiquer si un échange généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient des informations, les données de production, ou des données de test.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (X12)](../core/configuring-interchange-settings-x12.md)