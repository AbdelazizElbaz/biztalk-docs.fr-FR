---
title: "Réparer les Messages non analysées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unparsed messages
- repairing messages, unparsed messages
- messages, unparsed messages
ms.assetid: cc061243-3539-4407-a096-71a3feded1c5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de427afc854bf782f69a8c0428a874c61ffb5c4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-unparsed-messages"></a>Réparer les Messages non analysées
Si le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] désassembleur ne peut pas analyser un message, vous pouvez réparer ce message. Vous effectuez cette opération dans un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire depuis le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] site MRSR. Toutefois, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] traite ce message différemment à partir d’un message réparé la validation XML ou BRE a échoué.  
  
 Si un message ou un lot échoue à l’analyse, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] marque comme [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = True, avec un nombre d’erreurs d’analyse supérieur à 0. Le corps du message reste sous forme de fichier plat, entouré dans un wrapper XML. Si la règle de réparation est définie pour autoriser le traitement des échecs d’analyse, le message est envoyé à la boîte de réception non analysée pour le traitement à l’aide de la forme non analysée.  
  
 Il n'existe qu’une seule boîte de réception non analysée pour tous les utilisateurs et les départements, car [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] n’aient pas accès à toutes les données relatives au message autres que l’emplacement de réception de l’original. Par conséquent, pour réparer un message non analysé, un utilisateur doit disposer de la fonctionnalité de réparation et doit être associé au rôle de réparation dans tous les services.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Affiche le message non analysé dans la zone de texte de la Unparsed [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire. Pour corriger le problème d’analyse, vous pouvez entrer ou supprimer les caractères selon les besoins. Une fois qu’il est soumis, le message est extrait à partir du wrapper XML et renvoyé via le pipeline de réception SWIFT. Si l’analyse réussit, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] traite le message comme il le ferait tout autre message.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]ne traite pas d’un message non analysé que vous avez résolu via un flux de travail de réparation complète. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]envoie non vérifiés et approuvés. Lorsque vous signer un message non analysé réparé et l’envoyer, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ne pas appeler la validation de BRE ou vérifier le service, mais envoie le message directement au pipeline d’envoi. Si ce pipeline ne peut pas traiter le message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] envoie au processus de réparation.  
  
 Ce processus vous permet de résoudre les messages mal mis en forme d’un autre système. Toutefois, vous soyez prudent lors de la correction des problèmes d’analyse. Lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] traite un message non analysé, elle ne valide pas le message. Réparation non analysée n’étant pas définie en tant que rôle, toute personne peut effectuer cette procédure. Message non analysée n’appartiennent pas à n’importe quel service, la seule sécurité fournie sur l’accès à leur étant donné que les ACL de la boîte de réception non analysée. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]aussi, ne conserve pas l’original emplacement d’un message non analysé comme une propriété de contexte du message de réception.  
  
 Vous pouvez écrire une validation personnalisée à exécuter sur le message non analysé réparé. Vous pouvez également écrire un abonnement pour envoyer un message non analysé réparé au pipeline de fichier d’origine.  
  
 Pour le mécanisme de réparation travailler sur des messages non analysées, vous devez ajouter le schéma EnvelopeUnparsedMessage.xsd à l’assembly qui contient les schémas de message. Pour plus d’informations, consultez [déploiement des schémas A4SWIFT](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).