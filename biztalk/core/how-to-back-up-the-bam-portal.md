---
title: Comment sauvegarder le portail BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cea02e6-e387-4048-a1f3-d7c3c562f470
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e7308e54505c795e35ffa2fbb2d287c1a49ec4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-bam-portal"></a>Sauvegarde du portail BAM
Si vous utilisez l'analyse BAM (Business Activity Monitoring), vous devez sauvegarder le portail BAM dans le cadre de la sauvegarde de votre serveur BizTalk. Si vous n'utilisez pas l'analyse BAM, cette procédure est facultative.  
  
 Certaines phases du processus de sauvegarde diffèrent nettement selon la version d'Internet Information Services (IIS) que vous sauvegardez. IIS 6.0 permet de sauvegarder la configuration du pool d'applications et la configuration du site Web séparément. Vous pouvez également chiffrer les fichiers de sauvegarde de la configuration à l'aide d'un mot de passe.  
  
 IIS 7.0 enregistre les paramètres de configuration pour le pool d’applications et le site web dans un fichier applicationHost.config. Le fichier applicationHost.config n’est pas chiffré, mais les mots de passe de compte, le cas échéant, sont chiffrées dans le fichier. Le chiffrement est effectué à l'aide du certificat de l'ordinateur en cours de sauvegarde. Cette configuration ne peut pas être restaurée sur un autre ordinateur que celui dont elle provient.  
  
 Vous ne pouvez pas sauvegarder la configuration du portail BAM à l’aide du Gestionnaire IIS 7.0 ; Vous devez utiliser le **Appcmd.exe** outil de ligne de commande. Pour plus d’informations sur Appcmd, consultez [http://go.microsoft.com/fwlink/?LinkId=147497](http://go.microsoft.com/fwlink/?LinkId=147497).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
### <a name="to-back-up-the-bam-portal-iis-70"></a>Pour sauvegarder le portail BAM (IIS 7.0)  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
2.  Dans la boîte de dialogue Exécuter, dans la zone Ouvrir, tapez la commande suivante : `runas /user:` *Nom_Ordinateur*`\`*accountname* `cmd`, puis cliquez sur **OK** ou Appuyez sur **entrée**.  
  
     *AccountName* doit être un membre du groupe Administrateurs sur l’ordinateur local.  
  
3.  Lorsque vous y êtes invité, tapez le mot de passe *accountname*, puis appuyez sur **entrée**.  
  
4.  Type `cd %windir%\system32\inetsrv`, puis appuyez sur **entrée**.  
  
5.  Type `appcmd add backup “` *nom_sauvegarde*`”`, puis appuyez sur **entrée**.  
  
     Il n'est pas utile d'entrer un nom de sauvegarde. Si aucun nom n'est défini, il est généré automatiquement. « 20090224T123302 » est un exemple de nom de sauvegarde généré automatiquement.  
  
     Pour afficher une liste des sauvegardes de configuration existant, tapez `appcmd list backup`, puis appuyez sur **entrée**. Les sauvegardes créées par l’utilisateur sont enregistrés dans le **%windir%\system32\inetsrv\backup** active. Pour afficher la liste des options de sauvegarde fourni par **appcmd.exe**, type `appcmd backup /?`, puis appuyez sur **entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde d’un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)   
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)   
 [Portail BAM](../core/bam-portal.md)