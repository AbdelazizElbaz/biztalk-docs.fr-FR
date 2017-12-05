---
title: "Comment s’inscrire et supprimer BizTalk Assembly Viewer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f80b906-0a9e-4bcd-984d-db4550f2e51f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ad3628f61fec11f135bf2235f5e0d25f52992d3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-register-and-remove-the-biztalk-assembly-viewer"></a>Inscription et suppression de BizTalk Assembly Viewer
BizTalk Assembly Viewer n'est pas inscrit automatiquement lors de la configuration de BizTalk Server. Pour inscrire ou supprimer BizTalk Assembly Viewer, procédez comme suit :  
  
### <a name="to-add-assembly-viewer-to-the-windows-registry"></a>Pour ajouter Assembly Viewer au registre Windows  
  
1.  À partir de la **Démarrer** menu, cliquez sur **exécuter**.  
  
2.  Dans la boîte de dialogue Exécuter, tapez **cmd**.  
  
3.  À partir de la ligne de commande, accédez à \< *dossier d’Installation de BizTalk Server*\>\Developer Tools\ où BTSAsmExt.dll réside.  
  
4.  Sur la ligne de commande, tapez :  
  
     regsvr32 BTSAsmExt.dll  
  
5.  Pour commencer à utiliser Assembly Viewer, déconnectez-vous et reconnectez-vous sur l'ordinateur.  
  
### <a name="to-remove-assembly-viewer-from-the-windows-registry"></a>Pour supprimer Assembly Viewer du registre Windows  
  
1.  À partir de la **Démarrer** menu, cliquez sur **exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**.  
  
3.  À partir de la ligne de commande, accédez à \< *dossier d’Installation de BizTalk Server*\>\Developer Tools\ où BTSAsmExt.dll réside.  
  
4.  Sur la ligne de commande, tapez :  
  
     regsvr32/u BTSAsmExt.dll  
  
5.  Pour terminer la suppression, déconnectez-vous et reconnectez-vous sur l'ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des assemblys à l’aide de BizTalk Assembly Viewer](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)