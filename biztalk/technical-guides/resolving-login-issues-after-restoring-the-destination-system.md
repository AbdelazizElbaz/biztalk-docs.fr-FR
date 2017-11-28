---
title: "Résolution des problèmes de connexion après la restauration du système de Destination | Documents Microsoft"
description: "Envoi de journaux de script des connexions SQL Server pour résoudre des utilisateurs orphelins dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9232ca3-dadb-4b3c-8ec4-4e307c32d2e5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 559302718c9fe504c9c264de92f6a4af161d91f9
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="resolving-login-issues-after-restoring-the-destination-system"></a><span data-ttu-id="eaedd-103">Résolution des problèmes de connexion après la restauration du système de Destination</span><span class="sxs-lookup"><span data-stu-id="eaedd-103">Resolving Login Issues After Restoring the Destination System</span></span>

## <a name="orphaned-users"></a><span data-ttu-id="eaedd-104">Utilisateurs orphelins</span><span class="sxs-lookup"><span data-stu-id="eaedd-104">Orphaned users</span></span>
<span data-ttu-id="eaedd-105">Selon la façon dont le système source a été configuré au cours du déploiement, les utilisateurs « orphelins » peuvent doivent être résolus.</span><span class="sxs-lookup"><span data-stu-id="eaedd-105">Depending on how the source system was configured during deployment, "orphaned" users may need to be resolved.</span></span> <span data-ttu-id="eaedd-106">Un utilisateur orphelins de la base de données est un utilisateur qui ne dispose pas d’une sécurité correspondante login dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eaedd-106">An orphaned database user is a user who does not have a corresponding security login in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="eaedd-107">Créer des connexions correspondantes pour ces utilisateurs avant de mettre le système en ligne à l’aide de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SQL Management Studio (dans **sécurité**, **connexions**).</span><span class="sxs-lookup"><span data-stu-id="eaedd-107">Create corresponding logins for these users before bringing the system online using the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SQL Management Studio (in **Security**, **Logins**).</span></span> <span data-ttu-id="eaedd-108">Vous pouvez créer ces connexions à tout moment, mais nous vous recommandons de créer les lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d’envoi de journaux est configuré.</span><span class="sxs-lookup"><span data-stu-id="eaedd-108">You can create these logins at any point, but we recommend that you create them when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping is configured.</span></span>  
  
 <span data-ttu-id="eaedd-109">Les connexions qui sont créées doivent correspondre aux comptes Windows et les groupes qui ont été utilisées lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a été configuré sur le système source et à toutes les connexions qui ont été manuellement créées et utilisées dans tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-a créé le rôle.</span><span class="sxs-lookup"><span data-stu-id="eaedd-109">The logins that are created should correspond to the Windows accounts and groups that were used when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] was configured on the source system and to any logins that were manually created and used in any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-created role.</span></span> <span data-ttu-id="eaedd-110">Si ces connexions correspondent à des comptes Windows locaux ou de groupes, les comptes et les groupes doivent d’abord être créés avant que la connexion peut être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="eaedd-110">If these logins correspond to local Windows accounts or groups, the accounts and groups must first be created before the login can be added.</span></span> <span data-ttu-id="eaedd-111">Si le nom d’ordinateur du serveur BizTalk n’est pas modifié, puis résolvez les utilisateurs associés aux connexions pour les comptes et groupes locaux.</span><span class="sxs-lookup"><span data-stu-id="eaedd-111">If the computer name for the BizTalk server is not changed, then resolve the users associated with the logins for the local accounts and groups.</span></span>  
  
 <span data-ttu-id="eaedd-112">Lors de la configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction, vous pouvez [918992 de la base de connaissances : transférer les connexions et les mots de passe entre instances de SQL Server](https://support.microsoft.com/help/918992/how-to-transfer-logins-and-passwords-between-instances-of-sql-server) pour créer un script qui ajoute les connexions nécessaires pour le serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="eaedd-112">When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping, you can [KB 918992: Transfer the logins and the passwords between instances of SQL Server](https://support.microsoft.com/help/918992/how-to-transfer-logins-and-passwords-between-instances-of-sql-server) to create a script that adds the necessary logins to the destination server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaedd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaedd-113">See Also</span></span>  
 [<span data-ttu-id="eaedd-114">Résolution des problèmes de la copie des journaux de transaction</span><span class="sxs-lookup"><span data-stu-id="eaedd-114">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)
