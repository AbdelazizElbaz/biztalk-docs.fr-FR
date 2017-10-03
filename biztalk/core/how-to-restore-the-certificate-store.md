---
title: Comment restaurer le magasin de certificats | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c6f7551-d119-4668-9b52-6013f69a0302
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaeee6b762cf5af15ca7cba34864abd86682d4df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-the-certificate-store"></a>Restauration du magasin de certificats
Dans le cadre de la récupération de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez restaurer le magasin de certificats. Si vous récupérez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Édition Standard, vous devez utiliser cette procédure pour restaurer le magasin de certificats. Vous ne devez pas utiliser cette procédure pour récupérer d'autres éditions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] car le processus de récupération restaure automatiquement le magasin de certificats pour vous.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
### <a name="to-restore-the-certificate-store-biztalk-server-standard-edition"></a>Pour restaurer le magasin de certificats (BizTalk Server Édition Standard)  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, puis cliquez sur **Internet Explorer**.  
  
2.  Sur le **outils** menu, cliquez sur **Options Internet**.  
  
3.  Dans le **Options Internet** boîte de dialogue, cliquez sur le **contenu** onglet, puis cliquez sur **certificats**.  
  
4.  Dans le **certificats** boîte de dialogue, cliquez sur le **autres personnes** onglet, puis cliquez sur **importation**.  
  
5.  Dans le **Assistant Importation de certificat**, cliquez sur **Annuler**.  
  
     Cette opération crée le **carnet d’adresses** ruche dans le Registre.  
  
6.  Dans le **certificats** boîte de dialogue, cliquez sur **fermer**.  
  
7.  Dans le **Options Internet** boîte de dialogue, cliquez sur **OK**.  
  
8.  Cliquez sur **fichier**, puis cliquez sur **fermer** quitter Internet Explorer.  
  
9. Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.  
  
10. Dans l'Éditeur du Registre, accédez à la clé de Registre suivante :  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates**  
  
11. Vérifiez que le **carnet d’adresses** ruche est présent.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)