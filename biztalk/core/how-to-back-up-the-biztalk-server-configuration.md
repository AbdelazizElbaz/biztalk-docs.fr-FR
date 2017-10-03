---
title: Comment faire pour sauvegarder la Configuration de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f89050-c204-4d44-a875-299e690489ef
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad54aba8f8f49adeb8534bdbe28add15f0fe9638
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-biztalk-server-configuration"></a><span data-ttu-id="fe235-102">Sauvegarde de la configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fe235-102">How to Back Up The BizTalk Server Configuration</span></span>
<span data-ttu-id="fe235-103">Dans le cadre de la sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez sauvegarder les paramètres de configuration associés à l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe235-103">As part of backing up [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you should back up the configuration settings associated with the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="fe235-104">Le fait de disposer d'une copie des fichiers de configuration originaux simplifie grandement le processus de restauration en cas de défaillance matérielle impliquant le remplacement de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fe235-104">Having a copy of the original configuration file greatly simplifies the restoration process if you have a hardware failure that requires you to replace the computer.</span></span>  
  
 <span data-ttu-id="fe235-105">Les paramètres de configuration de chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont stockés dans un fichier XML créé par le gestionnaire de configuration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fe235-105">The configuration settings for each computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are stored in an XML file created by the BizTalk Server Configuration Manager.</span></span> <span data-ttu-id="fe235-106">Chaque fois que vous modifiez la configuration de vos serveurs BizTalk, vous devez exporter le fichier de configuration mis à jour vers votre emplacement de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="fe235-106">Any time you change the configuration of your BizTalk servers, you should export the updated configuration file to your backup location.</span></span> <span data-ttu-id="fe235-107">Ainsi, le fichier de configuration reste disponible si vous devez remplacer votre serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fe235-107">This helps to ensure that the configuration file is available if you have to replace your BizTalk server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe235-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="fe235-108">Prerequisites</span></span>  
 <span data-ttu-id="fe235-109">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fe235-109">You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.</span></span>  
  
### <a name="to-back-up-the-biztalk-server-configuration"></a><span data-ttu-id="fe235-110">Pour sauvegarder la configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fe235-110">To back up the BizTalk Server configuration</span></span>  
  
1.  <span data-ttu-id="fe235-111">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft BizTalk Server**, puis cliquez sur **Configuration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="fe235-111">Click **Start**, click **All Programs**, click **Microsoft BizTalk Server**, and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="fe235-112">Dans **Configuration de Microsoft BizTalk Server**, cliquez sur **exporter la Configuration**.</span><span class="sxs-lookup"><span data-stu-id="fe235-112">In **Microsoft BizTalk Server Configuration**, click **Export Configuration**.</span></span>  
  
3.  <span data-ttu-id="fe235-113">Dans le **Enregistrer sous** boîte de dialogue, accédez à l’emplacement où vous stockez vos sauvegardes.</span><span class="sxs-lookup"><span data-stu-id="fe235-113">In the **Save As** dialog box, browse to the location where you store your backups.</span></span>  
  
4.  <span data-ttu-id="fe235-114">Dans le **nom de fichier** zone, tapez un nom pour le fichier de configuration, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="fe235-114">In the **File name** box, type a name for the configuration file, and then click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe235-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe235-115">See Also</span></span>  
 <span data-ttu-id="fe235-116">[Sauvegarde d’un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="fe235-116">[Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="fe235-117">Comment récupérer la Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fe235-117">How to Recover the BizTalk Server Configuration</span></span>](../core/how-to-recover-the-biztalk-server-configuration.md)