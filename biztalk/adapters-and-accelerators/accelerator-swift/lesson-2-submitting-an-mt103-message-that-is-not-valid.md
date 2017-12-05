---
title: "Leçon 2 : Envoi d’un Message MT103 qui n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, invalid messages
- submitting, invalid messages
- submitting, MT103 messages
- MT103 messages
- messages, MT103 messages
ms.assetid: 4b070ae1-c400-421a-b2f6-b7b1f22c0e41
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d064c06aec2698da1be3824ec709dac1702f8e40
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-2-submitting-an-mt103-message-that-is-not-valid"></a>Leçon 2 : Envoi d’un Message MT103 qui n’est pas valide
Dans cette leçon, vous envoyez un message MT103 qui n’est pas valide, et puis vous résolvez l’erreur obtenu à l’aide des outils de votre système.  
  
### <a name="to-submit-an-mt103-message-that-is-not-valid"></a>Pour envoyer un message MT103 qui n’est pas valide  
  
1.  Copiez le fichier MT103_Invalid_Sample.txt à partir de \< *lecteur :*\>\Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial à \< *lecteur* \>: \Labs\Inbound\FlatFile dossier. Notez l’heure que vous déposez le fichier dans le dossier.  
  
2.  Ouvrez \< *lecteur :*\>\Labs\Outbound pour vérifier qu’aucun fichier XML correspondant à MT103_Invalid_Sample.txt n’est dans le dossier. (Le fichier XML correspondant au message MT103_Sample.txt valid doit toujours figurer dans ce dossier.)  
  
3.  Dans le bloc-notes, ouvrez le fichier MT103_Invalid_Sample.txt dans \< *lecteur :*\>\Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial.  
  
4.  Démarrer **Administration de BizTalk Server**.  
  
5.  Dans la Console Administration de BizTalk Server, développez **l’Observateur d’événements (Local)**, puis cliquez sur **Application**.  
  
6.  Recherchez une entrée d’erreur qui a une source de BizTalk Accelerator pour SWIFT et une heure qui correspond à lorsque vous déposez le message non valide dans le \< *lecteur*\>: \Labs\Inbound\FlatFile dossier. Double-cliquez sur cette entrée de l’erreur.  
  
7.  Dans la boîte de dialogue Propriétés de l’événement de l’erreur, vérifiez dans le volet Description que le message ayant échoué a été publié dans la MessageBox et le désassembleur SWIFT marqué **A4SWIFT_Failed** en tant que **True**. Fermez la boîte de dialogue Propriétés de l’événement.  
  
8.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, puis développez **groupe BizTalk**. Dans le **vue** menu, cliquez sur **Page Hub du groupe**.  
  
9. Dans le **vue d’ensemble du groupe** volet, dans le **Instances de Service suspendues groupées** volet, cliquez sur **regroupés par Application**.  
  
10. Dans le **Aperçu pour le résultat de la requête sélectionnée** volet, double-cliquez sur l’entrée **MT103_FlatFile_ReceivePort**.  
  
11. Dans la boîte de dialogue Détails du Service, cliquez sur le **Messages** onglet. Double-cliquez sur l’entrée dont le nom du Service est **MT103_FlatFile_ReceivePort**.  
  
12. Dans la boîte de dialogue Détails du Message, cliquez sur **corps** dans le volet gauche.  
  
13. Vérifiez que le message affiché dans le volet de corps de la boîte de dialogue Détails du Message correspond au MT103_Invalid_Sample.txt que vous avez ouvert dans le bloc-notes.  
  
 Passez à [leçon 3 : test d’une Instance XML](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md).