---
title: "Comment récupérer le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a5df99-6d03-4f1f-8540-1700d3a0b9db
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 781191047e0ee99b0000c7b773d46aa035a7e1d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-recover-the-bam-portal"></a>Récupération du portail BAM
Si vous utilisez l'analyse BAM, vous devez récupérer le portail BAM dans le cadre de la récupération de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous n'utilisez pas l'analyse BAM, cette procédure est facultative.  
  
 La procédure de récupération de la configuration du portail BAM diffère considérablement selon la version d'IIS que vous utilisez. Lorsque vous restaurez la configuration pour IIS 7, vous utilisez **Appcmd.exe**, et la restauration de la configuration pour le site Web par défaut entier, pas seulement le portail BAM.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
### <a name="to-recover-the-bam-portal-configuration-iis-70"></a>Pour récupérer la configuration du portail BAM (IIS 7.0)  
  
1.  Dans la boîte de dialogue Exécuter, dans la zone Ouvrir, tapez la commande suivante : `runas /user:` *Nom_Ordinateur*`\`*accountname* `cmd`, puis cliquez sur **OK** ou Appuyez sur **entrée**.  
  
     *AccountName* doit être un membre du groupe Administrateurs sur l’ordinateur local.  
  
2.  Lorsque vous y êtes invité, tapez le mot de passe *accountname*, puis appuyez sur **entrée**.  
  
3.  Type `cd %windir%\system32\inetsrv`, puis appuyez sur **entrée**.  
  
4.  Type `appcmd restore backup “` *nom_sauvegarde*`”`, puis appuyez sur **entrée**.  
  
     *Nom_sauvegarde* est le nom d’une sauvegarde que vous avez créé précédemment à l’aide de **Appcmd.exe**. Cette sauvegarde doit exister dans le **%windir%\system32\inetsrv\backup** active. Elle ne peut pas servir à récupérer les mots de passe créés sur un autre ordinateur. Si BAMAppPool est configuré pour s’exécuter sous une autre identité que la valeur par défaut **NetworkService** compte, vous devez configurer le compte et le mot de passe séparément, comme décrit dans l’étape suivante.  
  
5.  À l’aide de la **Gestionnaire des Services Internet (IIS)**, sélectionnez **Pools d’applications** dans les **connexions** volet.  
  
6.  Dans le **Pools d’applications** volet, avec le bouton droit le **BAMAppPool**, puis cliquez sur **paramètres avancés**  
  
7.  Dans le **paramètres avancés**boîte de dialogue, faites défiler jusqu'à la **modèle de processus** section. Cliquez sur le **identité** boîte. Un bouton représentant des points de suspension s'affiche à droite de la zone. Cliquez sur le **ellipses** bouton.  
  
8.  Dans le **identité du Pool d’applications** boîte de dialogue, cliquez sur le **compte personnalisé** , puis cliquez sur le **définir** bouton.  
  
9. Dans le **définir les informations d’identification** boîte de dialogue, entrez le nom de compte et un mot de passe pour BAMAppPool. Le nom du compte doit être entré en tant que *nom de l’ordinateur*`\`*accountname*, ou *domaine*`\`*accountname*. Cliquez sur **OK** pour fermer la **définir les informations d’identification** boîte de dialogue.  
  
10. Cliquez sur **OK** pour fermer la **identité du Pool d’applications** boîte de dialogue.  
  
11. Cliquez sur **OK** pour fermer la **paramètres avancés** boîte de dialogue.  
  
12. Vérifiez que le **BAMAppPool** est sélectionné dans la liste des pools d’applications. Dans le **Actions** volet à droite de la **Gestionnaire des Services Internet (IIS)** écran sous **tâches du Pool d’applications**, cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)   
 [Portail BAM](../core/bam-portal.md)