---
title: "Comment récupérer les alertes BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56c477b4-4605-4763-b20a-3baf4529f13f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec36491dd7368e0e2fdbcd8fb5abab9d840c6b1e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-recover-bam-alerts"></a><span data-ttu-id="09efe-102">Récupération des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="09efe-102">How to Recover BAM Alerts</span></span>
<span data-ttu-id="09efe-103">Si vous utilisez l'analyse BAM, vous devez récupérer les alertes BAM dans le cadre de la récupération de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09efe-103">As a part of recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], if you are using Business Activity Monitoring (BAM), you must also recover the BAM alerts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="09efe-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="09efe-104">Prerequisites</span></span>  
 <span data-ttu-id="09efe-105">Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="09efe-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-recover-bam-alerts-sql-server-2008"></a><span data-ttu-id="09efe-106">Pour récupérer les alertes d’analyse BAM (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="09efe-106">To recover BAM alerts (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="09efe-107">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.</span><span class="sxs-lookup"><span data-stu-id="09efe-107">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="09efe-108">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="09efe-108">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="09efe-109">**NSControl register - name BamAlerts-server***\<nom_serveur\>***-service - serviceusername «**  *\< ServiceUserName\>*  **« - servicepassword »**  *\<ServicePassword\>*  **»** </span><span class="sxs-lookup"><span data-stu-id="09efe-109">**nscontrol register -name BamAlerts -server**  *\<ServerName\>*  **-service -serviceusername "** *\<ServiceUserName\>* **" -servicepassword "** *\<ServicePassword\>* **"**</span></span>  
  
     <span data-ttu-id="09efe-110">Cette commande permet à Notification Services de se connecter à la base de données appropriée (ces informations sont conservées par nscontrol dans le Registre de l'ordinateur du service).</span><span class="sxs-lookup"><span data-stu-id="09efe-110">This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service computer by nscontrol).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="09efe-111">N’oubliez pas d’utiliser le nouveau serveur de bases de données des Services de Notification dans le **-server** option lors de la réinscription du service.</span><span class="sxs-lookup"><span data-stu-id="09efe-111">Remember to use the new Notification Services databases server in the **-server** option when re-registering the service.</span></span> <span data-ttu-id="09efe-112">Par ailleurs, vous devez conserver le même nom d'utilisateur pour le nouveau service Notification Services.</span><span class="sxs-lookup"><span data-stu-id="09efe-112">In addition, you should use the same user name for the new Notification Services service as the old one.</span></span>  
  
3.  <span data-ttu-id="09efe-113">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09efe-113">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="09efe-114">À l’invite de commandes, tapez : **net start NS$ BamAlerts**.</span><span class="sxs-lookup"><span data-stu-id="09efe-114">At the command prompt, type: **net start NS$BamAlerts**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09efe-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09efe-115">See Also</span></span>  
 [<span data-ttu-id="09efe-116">Récupération d’un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="09efe-116">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)