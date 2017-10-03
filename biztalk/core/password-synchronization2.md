---
title: La synchronisation2 de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, passwords
- passwords, synchronizing [SSO]
- managing [SSO], synchronizing passwords
- Password Synchronization [SSO]
- Password Synchronization [SSO], about Password Synchronization
- SSO database, passwords
ms.assetid: 6d4970e0-ac73-4fca-ab8f-6c8a6f3a6ec0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9c12bc9ff5190fe0a76c92b1cfee2233b9d206a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="password-synchronization"></a><span data-ttu-id="ade51-102">Synchronisation d’un mot de passe</span><span class="sxs-lookup"><span data-stu-id="ade51-102">Password Synchronization</span></span>
<span data-ttu-id="ade51-103">La fonction de la synchronisation de mots de passe consiste à simplifier l'administration de la base de données SSO et à synchroniser les mots de passe au sein des annuaires d'utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ade51-103">The purpose of Password Synchronization is to simplify administration of the SSO database, and to keep passwords in sync across user directories.</span></span>  
  
 <span data-ttu-id="ade51-104">Ces deux tâches sont effectuées par l'intermédiaire d'adaptateurs de synchronisation de mots de passe ; les rubriques de cette section présentent l'utilitaire de ligne de commande permettant de créer et de gérer ces adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="ade51-104">These two tasks are accomplished through the use of password synchronization adapters, and the topics in this section describe the command line utility for creating and managing those adapters.</span></span>  
  
 <span data-ttu-id="ade51-105">Il existe trois types de sous-fonctionnalités de synchronisation de mots de passe.</span><span class="sxs-lookup"><span data-stu-id="ade51-105">There are three types of password synchronization sub-features.</span></span>  
  
 <span data-ttu-id="ade51-106">Le premier type est **Windows vers externe** (par exemple, Active Directory vers RACF).</span><span class="sxs-lookup"><span data-stu-id="ade51-106">The first type is **Windows to External** (for example, Active Directory to RACF).</span></span> <span data-ttu-id="ade51-107">Dans ce scénario, une modification apportée à un mot de passe utilisateur Windows est capturée puis envoyée au serveur de l'authentification unique de l'entreprise assigné à la réception des modifications des mots de passe des contrôleurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="ade51-107">In this scenario, a Windows user's password change is captured and sent to the Enterprise SSO Server assigned to receive password changes from domain controllers.</span></span> <span data-ttu-id="ade51-108">Ce serveur transfère ensuite la modification du mot de passe à un système externe et le mappage dans la base de données SSO est synchronisé avec la modification apportée au système externe.</span><span class="sxs-lookup"><span data-stu-id="ade51-108">This then forwards the password change to an external system and the mapping in the SSO database is kept in sync with the change made on the external system.</span></span>  
  
 <span data-ttu-id="ade51-109">Le deuxième type est **externe vers Windows - synchronisation complète**.</span><span class="sxs-lookup"><span data-stu-id="ade51-109">The second type is **External to Windows - Full synchronization**.</span></span> <span data-ttu-id="ade51-110">Au cours de ce scénario, un mot de passe est capturé sur le système externe puis envoyé au serveur de l'authentification unique de l'entreprise assigné à la synchronisation des mots de passe. Celui-ci met à jour le mot de passe dans la base de données SSO ainsi que le mot de passe utilisateur Windows dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ade51-110">In this scenario, a password is captured on the External system and sent to the Enterprise Single Sign-On server assigned for Password Synchronization which then updates the password in the SSO database, and also updates the Windows user's password in Active Directory.</span></span>  
  
 <span data-ttu-id="ade51-111">Le troisième type **externe vers Windows - synchronisation partielle**.</span><span class="sxs-lookup"><span data-stu-id="ade51-111">The third type is **External to Windows - Partial synchronization**.</span></span> <span data-ttu-id="ade51-112">Lors de ce scénario, un mot de passe est capturé sur le système externe puis envoyé au serveur de l'authentification unique de l'entreprise assigné à la synchronisation des mots de passe. Celui-ci met à jour le mot de passe dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="ade51-112">In this scenario a password is captured on the External system and sent to the Enterprise Single Sign-On server assigned for Password Synchronization which then updates the password in the SSO database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ade51-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ade51-113">In This Section</span></span>  
  
-   [<span data-ttu-id="ade51-114">Comment installer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="ade51-114">How to Install Password Synchronization</span></span>](../core/how-to-install-password-synchronization.md)  
  
-   [<span data-ttu-id="ade51-115">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="ade51-115">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  
  
-   [<span data-ttu-id="ade51-116">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="ade51-116">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="ade51-117">Comment gérer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="ade51-117">How to Manage Password Synchronization</span></span>](../core/how-to-manage-password-synchronization.md)