---
title: "Étape 3 : Tester le dans lot scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c487d39d-b2be-41d4-963e-d0ee9ba169fb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d84c34eb3019f83ecd28f30425a93708affcecb2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-test-the-batch-inbatch-out-scenario"></a>Étape 3 : Tester le lot dans / lots scénario
Dans cette étape, vous testez le lot dans / hors lot didacticiel par la suppression du lot dans une instance de test / message du lot dans un dossier. Le port d’envoi que vous avez configurée envoie le message, il recevra le port de réception et le pipeline de réception traite et la placer dans le dossier de destination.  
  
### <a name="to-test-the-batch-inbatch-out-scenario"></a>Pour tester le traitement par lots dans / lots scénario  
  
1.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\<* lecteur*\>: \Batching Tutorial\Instances** dossier.  
  
2.  Bouton droit sur **BatchInBatchOut.txt**, puis cliquez sur **copie**.  
  
3.  Accédez à la  **\<* lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_ BTAHL7PickUp ** dossier.  
  
4.  Cliquez avec le bouton droit, puis cliquez sur **coller**.  
  
### <a name="to-verify-the-results-of-the-batch-inbatch-out-tutorial"></a>Pour vérifier les résultats du lot dans / Out didacticiel du lot  
  
-   À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\<* lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\ Dossier Tutorial\Tutorial_BTAHL7Drop ** de SDK\End en bout. Après une courte période, vous devez voir l’instance traitée du message de lot et un accusé de réception, apparaissent dans le dossier. Si elles n’apparaissent pas, vérifiez le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements pour un message d’erreur. Chaque fichier doit avoir un nom différent dans le formulaire \< *Guid*\>.txt.  
  
     Le premier message doit être le lot composé de deux messages. BizTalk Accelerator pour HL7 (BTAHL7) a inclus dans le fichier .txt les ces deux messages de manière séquentielle. Ce lot ne contient pas de FHS/recherche en texte intégral et les balises BHS/BTS. Un lot doit contenir soit toutes les balises FHS/FTS et BHS/BTS, like ou ce message de lot, aucun FHS/FTS et aucune balise BHS/BTS.  
  
    |MSH.9|MSH.10|MSH.3|MSH.5|  
    |-----------|------------|-----------|-----------|  
    |ADT ^ A03|000001|Tutorial_BatchSource|MESA_IS|  
    |ADT ^ A03|000002|Tutorial_BatchSource|MESA_IS|  
  
     Le second message doit être un accusé de réception unique application envoyé en réponse au message de lot, avec les champs suivants :  
  
    |MSH.9|MSH.3|MSH.5|MSA.1|MSA.2|  
    |-----------|-----------|-----------|-----------|-----------|  
    |L’ACCUSÉ DE RÉCEPTION ^ A03 ^ L’ACCUSÉ DE RÉCEPTION|MESA_IS|Tutorial_BatchSource|AA|000001|  
  
## <a name="see-also"></a>Voir aussi  
 [Partie 1 : Scénario de lot entrant fragmenté](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [Partie 3 : Scénario de création de lot](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)