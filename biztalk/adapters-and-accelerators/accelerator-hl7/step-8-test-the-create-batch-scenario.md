---
title: "Étape 8 : Tester le scénario de traitement par lots Créer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc7fac40-fd3e-413b-82cc-7ad08226094c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b7a77276e6246bb8fc525784309fded4bdf83f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-test-the-create-batch-scenario"></a>Étape 8 : Tester le scénario de traitement par lots Créer
Dans cette étape, vous testez le scénario de traitement par lots de créer en supprimant des instances de test des messages que vous voulez traiter par lot dans le dossier source du Tutorial_BTAHL7Pickup. Récupère le message à partir du dossier source que vous définissez le port d’envoi et l’envoie ; le port de réception reçoit et le pipeline de réception traite et le dépose dans le dossier de destination Tutorial_BTAHL7Drop.  
  
### <a name="to-test-the-create-batch-scenario"></a>Pour tester le scénario de traitement par lots de créer  
  
1.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\<* lecteur*> : \Batching Tutorial\Instances** dossier.  
  
2.  Sélectionnez **CreateBatchMessage1.txt**, et **CreateBatchMessage2.txt**, effectuez un clic droit, puis cliquez sur **copie**.  
  
3.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\<* lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\ Tutorial_BTAHL7Pickup ** dossier.  
  
4.  Cliquez avec le bouton droit, puis cliquez sur **coller**.  
  
### <a name="to-verify-the-results-of-the-create-batch-scenario"></a>Pour vérifier les résultats du scénario de traitement par lots de créer  
  
1.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\<* lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\ Tutorial_BatchACKDrop ** dossier. Après une courte période, vous devez voir l’instance traitée du lot d’accusé de réception s’affichent dans le dossier. Si elle n’apparaît pas, vérifiez le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements des messages d’erreur. Le fichier doit avoir le nom \< *Guid*> .txt. Ce lot doit contenir deux types de notifications générées lorsqu’il reçoit les deux messages qui ont été envoyés à l’origine. Ce lot doit avoir les champs suivants :  
  
    |FHS.5|BHS.5|BTS.1|FTS.1|  
    |-----------|-----------|-----------|-----------|  
    |Tutorial_BatchSource|Tutorial_BatchSource|2|1|  
  
     Les accusés de réception dans le lot doivent comporter les champs suivants :  
  
    |MSH.9|MSA.2|MSA.1|MSH.3|MSH.5|  
    |-----------|-----------|-----------|-----------|-----------|  
    |L’ACCUSÉ DE RÉCEPTION ^ A03 ^ L’ACCUSÉ DE RÉCEPTION|Msg01|AA|Tutorial_BatchDest|Tutorial_BatchSource|  
    |L’ACCUSÉ DE RÉCEPTION ^ A03 ^ L’ACCUSÉ DE RÉCEPTION|Msg02|AA|Tutorial_BatchDest|Tutorial_BatchSource|  
  
2.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\<* lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\ Tutorial_BatchMsgDrop ** dossier. Après une heure, vous devez voir l’instance traitée du lot à apparaissent dans le dossier. Si elle n’apparaît pas, vérifiez le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements des messages d’erreur. Le fichier doit avoir le nom \< *Guid*> .txt. Ce lot doit contenir les deux messages qui ont été envoyés à l’origine. Ce lot doit avoir les champs suivants :  
  
    |FHS.5|BHS.5|BTS.1|FTS.1|  
    |-----------|-----------|-----------|-----------|  
    |Tutorial_BatchDest|Tutorial_BatchDest|2|1|  
  
     Les messages du lot doivent comporter les champs suivants :  
  
    |MSH.9|MSH.10|MSH.3|MSH.5|  
    |-----------|------------|-----------|-----------|  
    |ADT ^ A03|Msg01|Tutorial_BatchSource|Tutorial_BatchDest|  
    |ADT ^ A03|Msg02|Tutorial_BatchSource|Tutorial_BatchDest|  
  
     Le lot est encapsulé dans deux ensembles d’en-têtes et codes de fin spécifique pour les lots :  
  
    -   En-tête de fichier et le code de fin (FHS et FT), qui sont utilisés pour placer un fichier qui peut comprendre plusieurs traitements. Notez l’application de réception de fichier (**Tutorial_BatchDest**) dans le champ FHS5 et la création du fichier date/heure dans FHS7. Notez le nombre de lots de fichiers (le nombre de lots dans le fichier) dans FTS2 (1).  
  
    -   En-tête de lot et le code de fin (BHS et BizTalk Server), qui sont utilisés pour placer chaque lot. Notez la réception d’application et le lot date/heure de création, comme dans le FHS et le nombre de messages par lots (2) dans BTS2 de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Partie 1 : Scénario de lot entrant fragmenté](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [Partie 3 : Scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)