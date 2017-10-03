---
title: "Configuration de la Validation (paramètres d’échange X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdad7016-1d66-4d11-b620-c28368f00133
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0edfe66791fa5c041c66a3adddde61730afe54ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-validation-x12-interchange-settings"></a>Configuration de la validation (Paramètres d'échange X12)
Les paramètres de génération et de validation d'un échange X12 définissent la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie l'existence de numéros de contrôle dupliqués dans l'échange reçu.  
  
> [!NOTE]
>  Les paramètres décrits dans cette rubrique s'appliquent également à la validation de l'échange HIPAA.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-validation"></a>Pour configurer la validation  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **Validation**.  
  
3.  Sélectionnez le **numéro de contrôle de l’échange** case à cocher pour activer le pipeline de réception bloquer les échanges en double. Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle (ISA13) de l'échange reçu ne correspond pas au numéro de contrôle de l'échange. Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.  
  
4.  Si **numéro de contrôle d’échange** est sélectionné, dans le **chercher isa13 en double dans** , entrez le nombre de jours pendant lesquels la vérification d’un échange en double sera effectuée à l’aide d’un spécifique numéro de contrôle d’échange.  
  
5.  Sélectionnez **numéro de contrôle du groupe** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle de groupe dupliqués (GS6).  
  
6.  Sélectionnez **numéro de contrôle de document informatisé** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle du document informatisé en double (ST2).  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (X12)](../core/configuring-interchange-settings-x12.md)