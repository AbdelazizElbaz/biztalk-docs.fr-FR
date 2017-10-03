---
title: "Étape 3e : générer et déployer la Solution BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbfc382b-ed4a-4401-9343-be1bffd747c9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a970a8f7adb450156b89849eb986c84fd05ab55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-build-and-deploy-the-biztalk-server-solution"></a>Étape 3e : générer et déployer la Solution BizTalk Server
Dans cette rubrique, nous allons déployer les deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projets (**BtsSalesforceIntegration** et **CustomPipeline**) que vous avez créée aux étapes précédentes.  
  
### <a name="to-build-and-deploy-the-biztalk-server-projects"></a>Pour générer et déployer des projets BizTalk Server  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **BtsSalesforceIntegration** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, puis cliquez sur **propriétés**.  
  
2.  Dans le **déploiement** onglet, pour **nom de l’Application**, entrez **SalesforceIntegration**. Cliquez sur **Enregistrer**.  
  
3.  Avec le bouton droit de la même façon, le **CustomPipeline** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, cliquez sur **propriétés**et dans le **déploiement** onglet, pour le **Application Nom** propriété, entrez **SalesforceIntegration** à nouveau. Cliquez sur **Enregistrer**. Cela garantit que le composant de pipeline personnalisé est déployé dans la même application que le **BtsSalesforceIntegration** projet.  
  
4.  Cliquez sur le nom de la solution dans l’Explorateur de solutions, puis cliquez sur **propriétés**. Dans la boîte de dialogue Pages de propriétés de Solution, cliquez sur **propriétés de Configuration**et vérifiez que le **générer** et **déployer** cases à cocher sont activées à la fois pour **BtsSalesforceIntegration** et **CustomPipeline** projets.  
  
5.  Cliquez sur le nom de la solution dans l’Explorateur de solutions, puis cliquez sur **générer la Solution**. Une fois la solution générée avec succès, cliquez à nouveau sur le nom de la solution, puis cliquez sur **déployer la Solution**. La solution est déployée dans la console d'administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer la Solution BizTalk Server dans Visual Studio](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)