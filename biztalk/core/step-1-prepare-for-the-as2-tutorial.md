---
title: "Étape 1 : Préparer le didacticiel AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3421c33b-0ccd-4e9d-b1c3-b161278e4d98
caps.latest.revision: "39"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75c6be6fb76debac7f5a143fa1616a999dee326c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-prepare-for-the-as2-tutorial"></a>Étape 1 : Préparer le didacticiel AS2
![Étape 1 sur 11](../core/media/tut-step1-of-11.gif "Tut_Step1_of_11")  
  
 Le didacticiel AS2 est exécuté sur un seul ordinateur. Pour préparer le didacticiel, vous devez installer et configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme décrit dans [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) section. Vous devez également ajouter une référence à l'application BizTalk Server EDI comme décrit dans cette rubrique. Les fichiers requis pour le didacticiel AS2 sont situés dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial.  
  
> [!NOTE]
>  Pour que ce didacticiel fonctionne, vous devez utiliser le même nom de connexion pour l'instance de l'hôte In-process et pour l'instance de l'hôte isolé.  
  
> [!NOTE]
>  Pour que ce didacticiel fonctionne, l'hôte BizTalk Server utilisé doit être marqué comme application 32 bits.  
  
> [!NOTE]
>  Pour que ce didacticiel fonctionne, il doit être exécuté sur une plateforme à l'aide d'IIS 7.0 ou d'IIS 7.5 et le paramètre Activer les applications 32 bits pour les pools d'applications doit être défini sur True.  
  
 Les dossiers du didacticiel 32 bits incluent trois dossiers dans lesquels [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] écrira les fichiers test de sortie (la charge EDI, le 997 et le MDN). Ces dossiers ont déjà été créés, mais vous devez définir les autorisations de sécurité pour deux des dossiers relatifs au 997 et au MDN (reportez-vous à la procédure ci-dessous).  
  
 Les dossiers et fichiers requis pour le didacticiel sont les suivants :  
  
|Dossier\Fichier|Fonction|  
|------------------|-------------|  
|\\_997ToFabrikam|Ce dossier vide est destiné à recevoir l'accusé de réception 997 renvoyé suite au traitement EDI. Il simule l'application émettrice du message EDI en provenance du tiers Fabrikam.|  
|\\_EDIXMLToContoso|Ce dossier vide est destiné à recevoir le fichier de charge XML après que BizTalk Server ait traité le message EDI. Il simule l'application sectorielle qui constitue la destination finale de la charge EDI.|  
|\\_MDNToFabrikam|Ce dossier vide est destiné à recevoir le message MDN renvoyé par BizTalk Server après le traitement AS2. Il simule une application du tiers Fabrikam.|  
|\Fabrikam|Ce dossier contient le fichier Default.aspx chargé d'enregistrer successivement le 997 dans le dossier _997ToFabrikam et le MDN dans le dossier _MDNToFabrikam.|  
|\Schemas|Ce dossier contient le schéma X12_00401_864.xsd ainsi que d'autres schémas utilisés par BizTalk lors du traitement du message EDI. Il contient également le projet Schemas.btproj que vous allez créer puis déployer dans l'optique de déployer les schémas.|  
|\Sender|Ce dossier contient le projet Sender.csproj que vous allez créer puis compiler dans le but de générer l'exécutable Sender.exe, lequel permet d'envoyer le message de test X12_00401_864.edi (situé dans le dossier \AS2 Tutorial) et de renvoyer le MDN.|  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-set-the-security-permission-for-the-997-and-mdn-folders"></a>Pour définir l'autorisation de sécurité pour les dossiers du 997 et du MDN  
  
1.  Dans l’Explorateur Windows, accédez à la [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam dossier. Cliquez sur le \\_997ToFabrikam dossier, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur le **sécurité** onglet, puis cliquez sur **modifier**. Dans le **autorisations** boîte de dialogue, cliquez sur **ajouter**.  
  
3.  Dans le **sélectionner des utilisateurs, les ordinateurs, les comptes de Service ou les groupes** boîte de dialogue, dans le volet de noms d’objet, entrez `Everyone`, puis cliquez sur **OK**.  
  
4.  Sélectionnez **tout le monde** dans les **noms d’utilisateur ou groupe** , cliquez sur la case à cocher **écrire** (sous la **autoriser** colonne) dans le **Autorisations** volet, puis cliquez sur **OK**.  
  
5.  Cliquez sur **OK**.  
  
6.  Répétez ces étapes pour le \\dossier _MDNToFabrikam.  
  
#### <a name="to-mark-the-biztalk-server-host-as-32-bit"></a>Pour marquer l'hôte BizTalk Server en tant qu'hôte 32 bits  
  
1.  > [!NOTE]
    >  Vous pouvez uniquement utiliser les pipelines AS2 dans un processus 32 bits. Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur un système d'exploitation 64 bits, les étapes suivantes doivent être effectuées de manière à marquer les processus de l'hôte en tant que processus 32 bits.  
  
     Sélectionnez **Démarrer**, sélectionnez **tous les programmes**, sélectionnez **Microsoft BizTalk Server**, puis sélectionnez **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, sélectionnez **paramètres de plateforme**, puis sélectionnez **hôtes**.  
  
3.  Dans le volet de détails, cliquez sur l’hôte in-process que vous souhaitez utiliser pour ce didacticiel, puis sélectionnez **propriétés**.  
  
4.  Dans le **propriétés de l’hôte** boîte de dialogue le **général** onglet, sélectionnez **32 bits seulement**, puis cliquez sur **OK**.  
  
5.  Répétez les étapes 3 et 4 pour l'hôte isolé.  
  
 Si BizTalk Server est installé sur un système d'exploitation 64 bits, vous devez également configurer IIS de manière à ce que celui-ci soit exécuté en mode 32 bits lors de l'exécution d'un processus hôte BizTalk 32 bits. Les instructions de configuration IIS sont présentées dans [étape 5 : configurer les Pages Web des partenaires commerciaux](../core/step-5-configure-the-trading-partner-web-pages.md), comme IIS vous permet de définir le processus de travail 32 bits sur un par pool d’application.  
  
#### <a name="to-add-reference-to-the-biztalk-edi-application"></a>Pour ajouter une référence à l’Application EDI BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **Applications** nœud, cliquez sur l’application que vous souhaitez utiliser pour EDI, telles que BizTalk Application 1. Pointez sur **ajouter**, puis cliquez sur Références.  
  
2.  Dans le **ajouter une référence d’Application** boîte de dialogue, sélectionnez **Application EDI BizTalk**, puis cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous déployez le schéma de l’exemple X12, comme décrit dans [étape 2 : créer et déployer l’exemple X12 schéma](../core/step-2-create-and-deploy-the-sample-x12-schema.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Didacticiel AS2](../core/tutorial-3-as2-tutorial.md)