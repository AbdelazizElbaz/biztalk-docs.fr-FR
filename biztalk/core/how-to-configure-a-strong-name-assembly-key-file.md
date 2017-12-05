---
title: "Comment configurer un fichier de clé de nom fort Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5778a8ec-f5f7-4ae1-a57e-99f6503f044c
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec807cf6b596f7e89f607ebeb56700c59134c211
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-strong-name-assembly-key-file"></a>Configuration d'un fichier de clé d'assembly de nom fort
Au cours du processus de déploiement d'une solution BizTalk, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] commence par créer les assemblys. Le processus de déploiement requiert la signature avec un nom fort de chaque assembly. Vous pouvez fortement signer vos assemblys en associant le projet avec un fichier de clé de nom fort assembly. Si ce n'est pas déjà fait, avant de déployer une solution à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], effectuez la procédure suivante pour générer un fichier de clé d'assembly de nom fort et l'attribuer à chaque projet de la solution.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez ouvrir une session à l'aide d'un compte membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Votre compte doit également disposer d'une autorisation en écriture sur le Global Assembly Cache (GAC). Le compte des administrateurs de l'ordinateur local dispose de cette autorisation.  
  
### <a name="to-configure-a-strong-name-assembly-key-file"></a>Pour configurer un fichier de clé d'assembly de nom fort  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  À l'invite de commandes, à partir du dossier dans lequel vous voulez stocker le fichier de clé, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
     **sn /k***nom_fichier* **.snk**   
  
     Exemple : **sn /k ErrorHandling.snk**  
  
     Un message de confirmation, **paire écrite dans la clé** \< *nom_fichier*\>**.snk** `,` affiche sur la ligne de commande.  
  
3.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur le projet, puis **propriétés**.  
  
4.  Cliquez sur le **signature** onglet et sélectionnez **Parcourir** dans les **choisir un fichier de clé de nom fort** zone déroulante.  
  
5.  Accédez au fichier de clé, puis cliquez dessus. Cliquez sur **ouvrez**, puis fermez les propriétés du projet.  
  
6.  Répétez les étapes 3 à 6 pour chaque projet dans la solution que vous souhaitez déployer à l’aide de ce fichier de clé de nom fort assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement des assemblys BizTalk à partir de Visual Studio dans une application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)