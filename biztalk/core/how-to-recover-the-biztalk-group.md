---
title: "Comment récupérer le groupe BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1010e55-7e3d-4565-8604-ea652ea4da8c
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deaf3ddae7d7351d53c5cd46b7d48633e0271a3d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-recover-the-biztalk-group"></a>Récupération du groupe BizTalk
Dans le cadre du processus de récupération du système, vous devez rejoindre un groupe BizTalk existant sur le serveur BizTalk Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
 Si vous récupérez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Édition Standard, vous devez télécharger un script facilitant la récupération du serveur. Télécharger [RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkID=195799).  
  
### <a name="to-recover-the-biztalk-group-standard-edition"></a>Pour récupérer le groupe BizTalk (Édition Standard)  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l'invite de commandes, tapez :  
  
     **RestoreConfig.vbe***\<SavedConfigXML  \>*  
  
     Où  *\<SavedConfigXML\>*  est le chemin d’accès complet et le nom du fichier de configuration enregistrée.  
  
     L'invite de commandes doit se fermer sans afficher d'erreur.  
  
    > [!NOTE]
    >  Pour récupérer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition sur un ordinateur 64 bits, vous devez exécuter **RestoreConfig.vbe** à partir de l’invite de commandes 32 bits afin qu’elle peut mettre à jour le Registre 32 bits. Pour ouvrir l’invite de commandes 32 bits, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **c:\windows\syswow64\cmd.exe**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le nom de l'ordinateur ayant échoué se trouve dans le fichier de la configuration enregistrée. Le nom de l'ordinateur sur lequel vous effectuez la restauration doit être identique à celui-ci. Vous devez exécuter le script décrit ci-dessus sur un ordinateur possédant ce nom. Toutefois, vous pouvez modifier le nom de l'ordinateur ayant échoué dans le fichier de la configuration enregistrée. Si vous procédez ainsi, vous pourrez exécuter le script précédent sur un ordinateur de nom différent.  
  
### <a name="to-recover-the-biztalk-group-developer-edition-or-enterprise-edition"></a>Pour récupérer le groupe BizTalk (Édition Développeur ou Édition Entreprise)  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.  
  
2.  Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], dans l’arborescence de la console, cliquez sur **groupe**.  
  
3.  Dans le volet détails, sélectionnez **joindre un groupe BizTalk existant**, puis spécifiez la base de gestion BizTalk (BizTalkMgmtDb) distante appropriée.  
  
4.  Cliquez sur **Appliquer la configuration**.  
  
5.  Cliquez sur **fichier**, puis cliquez sur **Exit**.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)