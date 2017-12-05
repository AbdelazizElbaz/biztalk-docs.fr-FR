---
title: Test de votre Installation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing installation
- installing, testing installation
ms.assetid: db27a75c-db7f-46ff-b8ef-2624ff18dcc8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7fc94930ba5ff0851114e36d728ee7f3ffb73ab
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="testing-your-installation"></a>Test de votre Installation
Vous pouvez configurer votre [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation en exécutant manuellement le didacticiel de bout en bout ou en exécutant le programme de didacticiel de bout en bout de test. Pour tester le programme, cliquez sur le **lancer le didacticiel** bouton pendant l’installation ou exécutez EndToEndTutorial.exe dans C:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\ Dossier didacticiel de bout en bout (après l’exécution de configuration et installation). Une de ces actions automatisées effectue les mêmes étapes que vous devez effectuer manuellement en exécutant le didacticiel. Le programme de didacticiel de bout en bout effectue les opérations suivantes :  
  
-   Déploie des schémas MSH et l’accusé de réception  
  
-   Déploie des schémas courants Version 2.3.1  
  
-   Déploie les schémas ADT  
  
-   Crée le Tutorial_1WayReceive port de réception  
  
-   Crée le Tutorial_MLLPReceive emplacement de réception  
  
-   Crée le Tutorial_BTAHL7PickUp port de réception  
  
-   Crée le Tutorial_FileReceiveLoc emplacement de réception  
  
-   Crée le port d’envoi Tutorial_sendAck_ADT  
  
-   Crée le port d’envoi Tutorial_sendMsg_RX  
  
-   Crée le port d’envoi Tutorial_BTAHL7Drop  
  
-   Crée le port d’envoi Tutorial_MLLPSend  
  
-   Crée le tiers Tutorial_ADTSystem  
  
-   Crée le tiers Tutorial_RXSystem  
  
-   Crée le tiers Tutorial_HISystem  
  
-   Redémarre le Service BizTalk  
  
 Si vous avez exécuté le programme de didacticiel de bout en bout, vous pouvez supprimer une instance de test pour HL7 dans un dossier prédéfini. Le pipeline de réception associé au dossier récupère le message et le traite. Selon les filtres, un pipeline d’envoi achemine le document dans le dossier de destination. Cette simple « aller-retour » exerce les blocs de construction de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) du moteur et confirme que votre installation.  
  
### <a name="to-test-your-installation"></a>Pour tester votre installation  
  
1.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator pour le dossier de didacticiel HL7\SDK\End en bout.  
  
2.  Cliquez sur le **TutorialSampleInstance.txt** de fichiers, puis cliquez sur **copie**.  
  
3.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_ BTAHL7PickUp dossier.  
  
4.  Cliquez avec le bouton droit, puis cliquez sur **coller**.  
  
5.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_ BTAHL7Drop dossier.  
  
     Vous pouvez vérifier si votre installation a réussi, si l’instance traité s’affiche dans le **Tutorial_BTAHL7Drop** dossier en tant que \< *Guid*\>.txt.  
  
 Passez à l’étape suivante, [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md).