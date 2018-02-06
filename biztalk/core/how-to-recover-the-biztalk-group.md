---
title: "Récupérer le groupe BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 01/30/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1010e55-7e3d-4565-8604-ea652ea4da8c
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3563956daa4848d4d67c1321c23676b21f9e4735
ms.sourcegitcommit: 78376935362715684b451eb6da9f2b1e8c129c2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-recover-the-biztalk-group"></a>Récupération du groupe BizTalk
Dans le cadre du processus de récupération du système, vous devez rejoindre un groupe BizTalk existant sur le serveur BizTalk Server.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
 Si vous récupérez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Édition Standard, vous devez télécharger un script facilitant la récupération du serveur. Télécharger [RestoreConfig.vbe](https://www.microsoft.com/download/details.aspx?id=7462).  
  
## <a name="recover-the-biztalk-group-standard-edition"></a>Récupérer le groupe BizTalk (Édition Standard)  
  
1.  Cliquez sur **Démarrer**, type **cmd**, puis sélectionnez **invite de commandes**.  
  
2.  À l'invite de commandes, tapez :  
  
     **RestoreConfig.vbe**  *\<SavedConfigXML\>*  
  
     Où  *\<SavedConfigXML\>*  est le chemin d’accès complet et le nom du fichier de configuration enregistrée.  
  
     L'invite de commandes doit se fermer sans afficher d'erreur.  
  
    > [!NOTE]
    >  Pour récupérer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition sur un ordinateur 64 bits, vous devez exécuter **RestoreConfig.vbe** à partir de l’invite de commandes 32 bits afin qu’elle peut mettre à jour le Registre 32 bits. Pour ouvrir l’invite de commandes 32 bits, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **c:\windows\syswow64\cmd.exe**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le nom de l'ordinateur ayant échoué se trouve dans le fichier de la configuration enregistrée. Le nom de l'ordinateur sur lequel vous effectuez la restauration doit être identique à celui-ci. Vous devez exécuter le script décrit ci-dessus sur un ordinateur possédant ce nom. Toutefois, vous pouvez modifier le nom de l'ordinateur ayant échoué dans le fichier de la configuration enregistrée. Si vous procédez ainsi, vous pourrez exécuter le script précédent sur un ordinateur de nom différent.  
  
## <a name="recover-the-biztalk-group-developer-edition-or-enterprise-edition"></a>Récupérer le groupe BizTalk (Developer Edition ou Enterprise Edition)  
  
1.  Ouvrez **Configuration de BizTalk Server** (menu Démarrer).
  
2.  Dans la console Administration de BizTalk Server, sélectionnez **groupe**.  
  
3.  Dans le volet détails, sélectionnez **joindre un groupe BizTalk existant**, puis entrez la base de données de gestion BizTalk (BizTalkMgmtDb) distante.  
  
4.  Sélectionnez **appliquer la Configuration**.  
  
5.  Sélectionnez **fichier**, puis sélectionnez **Exit**.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)
