---
title: "Configuration des propriétés de Validation de secours (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a64431d-373a-4d63-9b83-cbb323620152
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc6eb44f2ee4c2f9c63011dc14be41380c245996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-validation-properties-x12"></a>Configuration des propriétés de validation de secours (X12)
Les paramètres de secours de génération et de validation d'un échange X12 définissent la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie l'existence de numéros de contrôle dupliqués dans l'échange reçu.  
  
> [!NOTE]
>  Les paramètres décrits dans cette rubrique s'appliquent également à la validation de l'échange HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-validation"></a>Pour configurer la validation  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **Validation**.  
  
3.  Sélectionnez le **numéro de contrôle de l’échange** case à cocher pour activer le pipeline de réception bloquer les échanges en double. Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle (ISA13) de l'échange reçu ne correspond pas au numéro de contrôle de l'échange. Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.  
  
4.  Si **numéro de contrôle d’échange** est sélectionné, dans le **chercher isa13 en double dans** , entrez le nombre de jours pendant lesquels la vérification d’un échange en double sera effectuée à l’aide d’un spécifique numéro de contrôle d’échange.  
  
5.  Sélectionnez **numéro de contrôle du groupe** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle de groupe dupliqués (GS6).  
  
6.  Sélectionnez **numéro de contrôle de document informatisé** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle du document informatisé en double (ST2).  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 propriétés d’accord de secours pour le traitement de l’échange](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)