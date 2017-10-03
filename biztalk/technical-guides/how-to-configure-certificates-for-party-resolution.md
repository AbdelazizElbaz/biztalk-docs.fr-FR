---
title: "Comment configurer des certificats pour la résolution du tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 060101c1-14f3-4600-a18e-48a160d59bca
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 153c8ccce1fafbe32c51b1c048fad4081f5b0b0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-for-party-resolution"></a>Comment configurer des certificats pour la résolution du tiers
Lorsque vous utilisez l’Explorateur BizTalk pour configurer un tiers, vous pouvez configurer le tiers afin que le tiers est résolu à l’aide de sa signature numérique. Si vous configurez la partie de cette façon, lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message, il utilisera le certificat de clé publique pour déterminer qui a envoyé le message et pour résoudre l’expéditeur à un tiers connu dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-configure-party-resolution-to-use-a-certificate"></a>Pour configurer la résolution de tiers d’utiliser un certificat  
  
1.  Ouvrez le **propriétés de tiers** boîte de dialogue.  
  
2.  Cliquez sur le **certificat** onglet, puis cliquez sur **Parcourir**.  
  
3.  Sélectionnez un certificat.  
  
4.  Cliquez sur **OK**.