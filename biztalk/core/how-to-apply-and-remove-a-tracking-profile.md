---
title: "Comment appliquer et supprimer un modèle de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, testing
- tracking profiles, deleting
- testing, tracking profiles
ms.assetid: 77cef14b-c390-4da7-a383-b3abe414a168
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 955b2ccddb215b79fd7cdc7d51ed6f5160c297fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-apply-and-remove-a-tracking-profile"></a>Application et suppression d'un modèle de suivi
Une fois que vous avez créé ou modifié le modèle de suivi, l'étape suivante consiste à l'appliquer à une base de données de test et à en vérifier les résultats par le biais de tests intégrés. Vous pouvez lancer l'application du modèle de suivi depuis l'Éditeur de modèle de suivi ou en utilisant l'utilitaire de ligne de commande.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Un modèle de suivi créé à l'étape précédente et enregistré sur votre disque dur.  
  
### <a name="to-apply-the-tracking-profile-from-within-the-tpe"></a>Pour appliquer le modèle de suivi depuis l'Éditeur  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **éditeur**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Sur le **fichier** menu, cliquez sur **ouvrir**. Recherchez ensuite le fichier .btt approprié sur votre disque dur. Cliquez sur **ouvrir** à le charger.  
  
3.  Sur le **outils** menu, cliquez sur **appliquer le modèle de suivi** pour appliquer le fichier .btt à une base de données de gestion que vous avez définie à partir de la **définir la base de données de gestion** élément de menu dans le **Outils** menu. Vérifiez le résultat à l'aide du test intégré.  
  
4.  Avertissez la personne de votre organisation responsable du déploiement que les tests du modèle de suivi sont concluants et que le modèle est prêt à être déployé.  
  
### <a name="to-apply-the-tracking-profile-from-the-command-line"></a>Pour appliquer le modèle de suivi à partir de l'utilitaire de ligne de commande  
  
-   À l'invite de commandes, exécutez l'outil dont le fichier bttdeploy.exe est situé dans le dossier \Tracking comme suit :  
  
    ```  
    bttdeploy.exe <profile name>.btt  
    ```  
  
> [!NOTE]
>  Vous devez disposer des privilèges d'administrateur BizTalk pour utiliser cet outil.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
> [!IMPORTANT]
>  Au cours du déploiement, l'outil bttdeploy vérifie la version d'assembly contenue dans les modèles de suivi et la compare à la version de l'assembly déployé. Cet outil échoue si l'assembly n'est pas déployé au moment de son exécution.  
  
> [!IMPORTANT]
>  Lors de l'application d'un modèle de suivi à l'aide d'un utilitaire de ligne de commande, l'outil bttdeploy applique le modèle à la base de données de gestion BizTalk que vous avez indiquée lorsque vous avez exécuté l'Assistant Configuration. Si vous indiquez une base de données différente pour l'option Définir la base de données de gestion dans l'Éditeur de modèle de suivi, elle est utilisée. Si vous spécifiez un serveur et une base de données de gestion pour l'option de la ligne de commande de bttdeploy, cette option écrase toutes les autres. Pour plus d’informations sur l’utilisation de bttdeploy, consultez [utilitaire](../core/tracking-profile-deployment-utility.md).  
  
### <a name="to-remove-a-tracking-profile"></a>Pour supprimer un modèle de suivi  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **éditeur**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Sur le **fichier** menu, cliquez sur **ouvrir**. Recherchez ensuite le fichier .btt approprié sur votre disque dur. Cliquez sur **ouvrir** à le charger.  
  
3.  Sur le **outils** menu, cliquez sur **supprimer le modèle de suivi** pour supprimer le modèle de suivi basé sur le fichier .btt à partir de la base de données de gestion BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles de suivi](../core/creating-tracking-profiles.md)