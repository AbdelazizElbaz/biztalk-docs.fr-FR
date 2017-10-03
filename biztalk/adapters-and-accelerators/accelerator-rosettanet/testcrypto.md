---
title: TestCrypto | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, TestCrypto utility
- troubleshooting, TestCrypto utility
- TestCrypto utility
ms.assetid: 02768794-64ac-4d99-930c-738bed9626c5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e9d3314b5564ab7619744e97f8e63df55683117
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="testcrypto"></a>TestCrypto
Vous utilisez l’utilitaire TestCrypto pour résoudre les échecs de déchiffrement des messages. L’utilitaire indique si le déchiffrement échoue. Si le déchiffrement réussisse, l’utilitaire indique que le certificat est et affiche le message déchiffré.  
  
 Vous exécutez TestCrypto sur un fichier qui contient uniquement la partie chiffrée du message, sans les en-têtes non chiffrés. Extraire l’objet binaire volumineux (BLOB) de chiffré du message dans un fichier texte, en espionnant le message entrant ou en récupérant le message à partir de `MessageStorageIn`.  
  
 Pour plus d’informations sur la récupération d’un message à partir de `MessageStorageIn`, consultez [GetMessages exemple](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md).  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK  
  
## <a name="running-testcrypto"></a>TestCrypto en cours d’exécution  
  
#### <a name="to-run-testcrypto"></a>Pour exécuter TestCrypto  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Accessoires**, puis cliquez sur **invite de commandes**.  
  
2.  Déplacer vers \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK.  
  
3.  À l’invite de commandes, tapez **TestCrypto.exe \<nom de fichier >**, puis appuyez sur ENTRÉE.  
  
## <a name="remarks"></a>Notes  
 Le déchiffrement échoue si le certificat que l’utilitaire de recherche n’est pas le certificat requis et valid, ou si l’utilitaire ne peut pas trouver le certificat.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)