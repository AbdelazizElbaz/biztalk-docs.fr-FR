---
title: "Nouveau traitement de Service d’envoi et de réparation de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages, MrsrRepair orchestration
- orchestrations, MrsrRepair orchestration
- InfoPath forms, valid forms
- messages, BAS
- unparsed messages
- repairing messages, unparsed messages
- messages, unparsed messages
- messages, InfoPath forms
- Business Rule Engine
- MrsrRepair orchestration
- InfoPath forms, messages
- BAS, messages
ms.assetid: fe2ee009-bf63-4bc0-b231-ad8a2633719f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: add084f335f2ca3bd816af7a743327e77cbecca1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission-service-processing"></a>Nouveau traitement de Service d’envoi et de la réparation de message
L’orchestration MrsrRepair gère toutes les opérations de Message Repair et New Submission, notamment le traitement de la commande suivante :  
  
-   Messages nécessitant une réparation  
  
-   Messages non analysées  
  
-   Nouveaux messages créés dans le site MRSR  
  
## <a name="processing-messages-requiring-repair"></a>Le traitement des Messages nécessitant une réparation  
 Si un message doit être réparé, l’orchestration est avertie que le message entrant provient le désassembleur. Il traite uniquement les messages en provenance le désassembleur si la valeur de la capacité de rôle permettant de créer ou de réparation. L’orchestration MrsrRepair s’abonne aux messages à partir de la MessageBox qui ont les propriétés suivantes :  
  
```  
A4SWIFT_Failed==true AND  
BTS_Operation=="A4SWIFT_DasmMarkedAsFailed" AND  
A4SWIFT_SwiftBound==true  
```  
  
 Le port d’entrée de la MrsrRepair orchestration utilisée pour Message Repair et New Submission est liée à la STS.Outbox.Location emplacement de réception. Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] le programme d’installation installe les programme cet emplacement par de réception par défaut. Lors de la réception de messages d’envoi aux utilisateurs sur le site MRSR, cela emplacement prélève les messages et les transfère vers l’orchestration MrsrRepair.  
  
 Le tableau suivant répertorie les valide [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms :  
  
|[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]Formulaires||||||  
|------------------------------------------------------------------------------|------|------|------|------|------|  
|MT010|MT011|MT012|MT015|MT019|MT020|  
|MT021|MT022|MT023|MT028|MT029|MT030|  
|MT031|MT032|MT035|MT036|MT037|MT039|  
|MT041|MT042|MT043|MT044|MT045|MT046|  
|MT047|MT048|MT049|MT050|MT051|MT052|  
|MT055|MT056|MT057|MT059|MT061|MT062|  
|MT063|MT064|MT065|MT066|MT067|MT068|  
|MT069|MT072|MT073|MT074|MT075|MT076|  
|MT077|MT081|MT082|MT083|MT085|MT087|  
|MT090|MT092|MT094|MT102|MT102PLUS|MT103|  
|MT103Plus|MT104|MT105|MT106|MT107|MT110|  
|MT111|MT112|MT121|MT190|MT191|MT192|  
|MT195|MT196|MT198|MT199|MT200|MT201|  
|MT202|MT203|MT204|MT205|MT206|MT207|  
|MT210|MT256|MT290|MT291|MT292|MT295|  
|MT296|MT298|MT299|MT300|MT303|MT304|  
|MT305|MT306|MT307|MT308|MT320|MT321|  
|MT330|MT340|MT341|MT350|MT360|MT361|  
|MT362|MT364|MT365|MT380|MT381|MT390|  
|MT391|MT392|MT395|MT396|MT398|MT399|  
|MT400|MT405|MT410|MT412|MT416|MT420|  
|MT422|MT430|MT450|MT4555|MT456|MT490|  
|MT491|MT492|MT495|MT496|MT498|MT499|  
|MT500|MT501|MT502|MT503|MT504|MT505|  
|MT506|MT507|MT508|MT509|MT510|MT513|  
|MT514|MT515|MT516|MT517|MT518|MT519|  
|MT524|MT526|MT527|MT528|MT529|MT535|  
|MT536|MT537|MT538|MT540|MT541|MT542|  
|MT543|MT544|MT545|MT546|MT547|MT548|  
|MT549|MT558|MT559|MT564|MT565|MT566|  
|MT567|MT568|MT569|MT574_IRSLST|MT574_W8BENO|MT575|  
|MT576|MT577|MT578|MT579|MT581|MT582|  
|MT584|MT586|MT587|MT588|MT589|MT590|  
|MT591|MT592|MT595|MT596|MT598|MT599|  
|MT600|MT601|MT604|MT605|MT606|MT607|  
|MT643|MT644|MT645|MT646|MT649|MT690|  
|MT691|MT692|MT695|MT696|MT698|MT699|  
|MT700|MT701|MT705|MT707|MT710|MT711|  
|MT720|MT721|MT730|MT732|MT734|MT740|  
|MT742|MT747|MT750|MT752|MT754|MT756|  
|MT760|MT767|MT768|MT769|MT790|MT791|  
|MT792|MT795|MT796|MT798|MT799||  
|MT800|MT801|MT802|MT810|MT812|MT813|  
|MT820|MT821|MT822|MT823|MT824|MT890|  
|MT891|MT892|MT895|MT896|MT898|MT899|  
|MT900|MT910|MT920|MT935|MT940|MT941|  
|MT942|MT950|MT960|MT961|MT962|MT963|  
|MT964|MT965|MT966|MT967|MT970|MT971|  
|MT972|MT973|MT985|Mt986|MT990|MT991|  
|MT992|MT995|MT996|MT998|MT999||  
  
## <a name="processing-unparsed-messages"></a>Le traitement des Messages non analysées  
 Si l’orchestration MrsrRepair détermine qu’un message n’a pas pu être analysé, elle définit les indicateurs appropriés, puis envoie le message à la MRSR la boîte de réception de site à réparer dans le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour les messages non analysées. Lorsque l’orchestration reçoit le message après la réparation, il définit le BTS. Propriété opération «[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRCompleted » et le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]propriété _Failed sur False, puis achemine le message vers la MessageBox. Ces propriétés garantissent que le message non analysé réparé n’entre pas dans le processus de réparation de message à nouveau.  
  
 L’écran de réparation non analysée est appelé **Message non analysée**.  
  
## <a name="processing-new-messages-created-in-mrsr"></a>Traitement des nouveaux Messages créés dans MRSR  
 Si le message reçu par l’orchestration MrsrRepair a été créé dans le site MRSR, l’orchestration est avertie que le message entrant provient [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] (pas le désassembleur), et que le message a été signé.  
  
## <a name="common-operations"></a>Opérations courantes  
 L’orchestration MrsrRepair effectue une série d’opérations courantes sur tous les messages, qu’ils doivent réparation, n’a pas pu être analysés. ou sont de nouveaux messages. L’orchestration exécute une boucle qui effectue les opérations courantes pour chaque étape du flux de travail, y compris la vérification de changement de clé, créer, réparer et approuver. Cette orchestration est utilisée, quel que soit le service et les rôles.  
  
 Ces étapes courantes sont les suivantes :  
  
1.  Placez le message dans un formulaire d’enveloppe.  
  
2.  Envoyer le message au site MRSR.  
  
3.  Le message (après les actions utilisateur) à partir du site MRSR via la STS.Outbox.Location emplacement de réception. Si un délai d’attente se produit, l’orchestration gère le délai d’attente. Si le délai d’attente se produit lors de l’utilisateur est la réparation, vérification ou l’approbation d’un message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] renvoie le message à la boîte de réception de la réparation, la réinitialisation du flux de travail à l’étape de réparation.  
  
    > [!NOTE]
    >  Le port d’entrée de la MrsrRepair orchestration utilisée pour Message Repair et New Submission est liée à la STS.Outbox.Location emplacement de réception. Cet emplacement de réception doit être en cours d’exécution sur un hôte BizTalk qui est lié aux serveurs sur lesquels le site MRSR sur lesquels est installé. Cet ordinateur hôte est en général BizTalkServerApplication, mais il peut être un autre ordinateur hôte. S’il est un hôte différent, vous devez vérifier que les serveurs à laquelle est lié l’hôte ont site MRSR sur lesquels est installé.  
  
4.  Vérifiez que la signature entrée par l’utilisateur est appropriée pour le rôle et stocker cette signature pour vérifier les restrictions de rôle.  
  
5.  Si le contenu du message a été stocké à une étape précédente, comparez le contenu provenant du site MRSR avec le message stocké. L’orchestration dans le cas le message n’est pas une correspondance.  
  
6.  Le message d’échouer si l’utilisateur a rejeté les modifications.  
  
7.  Effectuer la validation XSD et BRE sur le message si l’utilisateur accepte les modifications.  
  
8.  Le cas échéant, passer à l’étape suivante.  
  
## <a name="customizing-the-repair-orchestration"></a>Personnalisation de l’Orchestration de réparation  
 Vous pouvez personnaliser l’orchestration MrsrRepair en ajoutant des fonctionnalités de pré-traitement ou de post-traitement. Par exemple, vous pourriez ajouter une orchestration pour les étapes de prétraitement, ou ajouter une forme d’orchestration avant de la forme envoi existant pour promouvoir une propriété. Toutefois, vous ne peut pas créer ou modifier des accords ou des profils associés Message Repair et New Submission, étant donné que l’orchestration MrsrRepair ne serait pas informée. Vous ne pouvez pas ajouter de nouvelles définitions de rôle au-delà réparateur, le créateur, vérificateur ou approbateur. Vous ne peut pas modifier la structure, ou ajouter des fonctionnalités à la base, de l’orchestration.  
  
## <a name="business-rules-policies"></a>Stratégies de règles d’entreprise  
 Pour le processus de réparation, l’orchestration de réparation appelle le moteur de règles métier BizTalk (BRE) pour charger la stratégie de référence pour le type de message, par exemple, MT103_Master_Policy.xml. L’orchestration transmet le moteur BRE le type de message et le corps. La stratégie de principal du message contient une liste de toutes les autres stratégies qui se rapportent à ce type de message. Le moteur BRE charge toutes les stratégies pour le type de message. Ces stratégies incluent SWIFT_Reference_Policy, SWIFT_PartyIdentifier_Policy, les stratégies de règles de réseau et la stratégie de validation spécifique au type de message. Le moteur BRE exécute toutes les stratégies répertoriées dans la stratégie de référence, indépendamment des erreurs et retourne toutes les erreurs.