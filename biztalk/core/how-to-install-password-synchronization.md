---
title: Comment installer la synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, Password Synchronization [SSO]
- Password Synchronization [SSO], installing
ms.assetid: 8ace0401-b759-4ea3-91a0-be2aa8b5a5a4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ecc01ef4bc9d8bf2e82ca3dfe23b13ea0b67be2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-password-synchronization"></a><span data-ttu-id="7a68d-102">Comment installer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="7a68d-102">How to Install Password Synchronization</span></span>
<span data-ttu-id="7a68d-103">À l'instar des autres fonctionnalités d'authentification unique, la synchronisation de mot de passe n'est pas installée par défaut avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et doit être sélectionnée lors de l'installation.</span><span class="sxs-lookup"><span data-stu-id="7a68d-103">As with the other Single Sign-On features, Password Synchronization is not installed in the default [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation, and must be specifically selected during setup.</span></span>  
  
### <a name="to-install-password-synchronization"></a><span data-ttu-id="7a68d-104">Pour installer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="7a68d-104">To install Password Synchronization</span></span>  
  
1.  <span data-ttu-id="7a68d-105">Sur le CD-ROM de BizTalk Server, accédez à la  **\<CDRoot > \Platforms\SSO** dossier.</span><span class="sxs-lookup"><span data-stu-id="7a68d-105">On the BizTalk Server CD, browse to the **\<CDRoot>\Platforms\SSO** folder.</span></span>  
  
2.  <span data-ttu-id="7a68d-106">Exécutez **setup.exe** et suivez les instructions de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="7a68d-106">Run **setup.exe** and follow the instructions in the wizard.</span></span>  
  
3.  <span data-ttu-id="7a68d-107">Sélectionnez le **synchronisation de mot de passe** de fonctionnalité et de poursuivre l’installation.</span><span class="sxs-lookup"><span data-stu-id="7a68d-107">Select the **Password Synchronization** feature and proceed with the installation.</span></span>  
  
 <span data-ttu-id="7a68d-108">Les adaptateurs de synchronisation de mot de passe sont également nécessaires pour envoyer et recevoir les modifications de mot de passe via le système externe.</span><span class="sxs-lookup"><span data-stu-id="7a68d-108">In addition to this, Password synchronization adapters are necessary to send and receive password changes to the external system.</span></span> <span data-ttu-id="7a68d-109">Les rubriques de cette section décrivent la configuration de vos propres adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="7a68d-109">The topics in this section describe how to configure your own adapters.</span></span>  
  
 <span data-ttu-id="7a68d-110">Vous pouvez également contacter les alias de support pour obtenir des informations sur les adaptateurs de synchronisation de mot de passe disponibles.</span><span class="sxs-lookup"><span data-stu-id="7a68d-110">You can also contact support aliases to obtain information on available Password synchronization adapters.</span></span>  
  
 <span data-ttu-id="7a68d-111">Enfin, outre la fonctionnalité de synchronisation de mot de passe du service d'authentification unique de l'entreprise (ENTSSO), des composants doivent être installés sur les contrôleurs de domaine pour capturer les modifications de mot de passe effectuées dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7a68d-111">Finally, to capture password changes made in Active Directory, in addition to installing the ENTSSO Password Sync feature, components need to be installed on the domain controllers to capture password changes.</span></span>  
  
 <span data-ttu-id="7a68d-112">Le composant de capture de mot de passe Windows et le service de notification de modification de mot de passe (PCNS, Password Change Notification Service) doivent être installés sur tous les contrôleurs de domaine pour lesquels les mots de passe seront capturés.</span><span class="sxs-lookup"><span data-stu-id="7a68d-112">Both the Windows Password Capture component and Password Change Notification Service (PCNS) must be installed on all domain controllers from which you will be capturing passwords.</span></span> <span data-ttu-id="7a68d-113">Vous pouvez télécharger ces composants à l'adresse suivante :</span><span class="sxs-lookup"><span data-stu-id="7a68d-113">You can install these components from the following location:</span></span>  
  
 [<span data-ttu-id="7a68d-114">http://go.Microsoft.com/fwlink/?LinkId=68145</span><span class="sxs-lookup"><span data-stu-id="7a68d-114">http://go.microsoft.com/fwlink/?LinkId=68145</span></span>](http://go.microsoft.com/fwlink/?LinkId=68145)  
  
 <span data-ttu-id="7a68d-115">Consultez la documentation associée (également située dans ce dossier) avant de procéder à l'installation sur le contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="7a68d-115">Read the accompanying documentation (also located in this folder) before you proceed with the installation on the domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a68d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a68d-116">See Also</span></span>  
 [<span data-ttu-id="7a68d-117">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="7a68d-117">Password Synchronization</span></span>](../core/password-synchronization2.md)