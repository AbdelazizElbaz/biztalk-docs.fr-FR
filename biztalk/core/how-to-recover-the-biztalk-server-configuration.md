---
title: "Comment récupérer la Configuration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d39e50-4296-49c7-bd1e-63b1325af168
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9935c2c565d78d0bc102d4aef86959c2a9066e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-recover-the-biztalk-server-configuration"></a><span data-ttu-id="2cfe9-102">Récupération de la configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2cfe9-102">How to Recover the BizTalk Server Configuration</span></span>
<span data-ttu-id="2cfe9-103">Dans le cadre de la restauration de votre serveur BizTalk, vous devez également importer le fichier de configuration créé lors de l'installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-103">As part of recovering your BizTalk server, you must also import the configuration file that you created when you installed BizTalk Server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2cfe9-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2cfe9-104">Prerequisites</span></span>  
 <span data-ttu-id="2cfe9-105">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-105">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-recover-the-biztalk-server-configuration"></a><span data-ttu-id="2cfe9-106">Pour récupérer la configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2cfe9-106">To recover the BizTalk Server configuration</span></span>  
  
1.  <span data-ttu-id="2cfe9-107">À l'aide du Bloc-notes, modifiez le fichier de configuration de BizTalk Server que vous aviez préalablement sauvegardé, puis entrez les mots de passe pour les comptes d'utilisateur de tous les services BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-107">Using Notepad, edit the BizTalk Server configuration file that you previously backed up, and enter the user account passwords for all of the BizTalk Server services.</span></span>  
  
2.  <span data-ttu-id="2cfe9-108">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-108">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
3.  <span data-ttu-id="2cfe9-109">Dans **Configuration de Microsoft BizTalk Server**, cliquez sur **importer la Configuration**.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-109">In **Microsoft BizTalk Server Configuration**, click **Import Configuration**.</span></span>  
  
     <span data-ttu-id="2cfe9-110">Vérifiez qu'aucune icône d'invalidation ne s'affiche devant un composant.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-110">Verify that there are no invalidation icons appearing in front of any feature.</span></span> <span data-ttu-id="2cfe9-111">Si l'un d'entre eux rencontre des erreurs de configuration, vous devez les corriger dès maintenant.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-111">If any of the features have configuration errors, now is the time to correct them.</span></span>  
  
4.  <span data-ttu-id="2cfe9-112">Cliquez sur **Appliquer la configuration**.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-112">Click **Apply Configuration**.</span></span>  
  
     <span data-ttu-id="2cfe9-113">Après avoir configuré tous les composants de BizTalk Server, fermez la fenêtre de configuration.</span><span class="sxs-lookup"><span data-stu-id="2cfe9-113">After all of the BizTalk Server features are configured, close the configuration window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cfe9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cfe9-114">See Also</span></span>  
 <span data-ttu-id="2cfe9-115">[Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="2cfe9-115">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="2cfe9-116">Comment faire pour sauvegarder la Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2cfe9-116">How to Back Up The BizTalk Server Configuration</span></span>](../core/how-to-back-up-the-biztalk-server-configuration.md)