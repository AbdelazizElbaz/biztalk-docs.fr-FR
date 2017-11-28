---
title: "Installation des problèmes connus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2f80ff9-b37c-49f8-8250-fcf3cec4c0fc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf4e9197d2b3c448b4fd9cc42c0cdeb929917061
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installation-known-issues"></a><span data-ttu-id="f8199-102">Installation des problèmes connus</span><span class="sxs-lookup"><span data-stu-id="f8199-102">Installation known issues</span></span>
<span data-ttu-id="f8199-103">Des informations utiles qui peuvent vous aider à éviter les problèmes d’installation.</span><span class="sxs-lookup"><span data-stu-id="f8199-103">Useful information that may help you avoid installation problems.</span></span>  
  
## <a name="prerequisites-for-installing-btahl7"></a><span data-ttu-id="f8199-104">Conditions préalables pour l’installation BTAHL7</span><span class="sxs-lookup"><span data-stu-id="f8199-104">Prerequisites for installing BTAHL7</span></span>  
 <span data-ttu-id="f8199-105">Les conditions préalables pour l’installation [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] incluent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f8199-105">The prerequisites for installing [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] include the following:</span></span>  
  
-   <span data-ttu-id="f8199-106">Composants de base de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], y compris Enterprise Single Sign-On (SSO), de groupe et de Runtime, doit être configuré.</span><span class="sxs-lookup"><span data-stu-id="f8199-106">Basic components of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], including Enterprise Single Sign-On (SSO), Group, and Runtime, should be configured.</span></span>  
  
-   <span data-ttu-id="f8199-107">L’utilisateur de l’installation et la configuration de BTAHL7 doit être membre du groupe Administrateurs de BizTalk et un membre du groupe Administrateurs sur le serveur SQL Server où sont stockées les données BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="f8199-107">The user installing and configuring BTAHL7 must be a member of the BizTalk Administrators group, and a member of the Administrators group on the SQL Server where the BTAHL7 data is stored.</span></span>
  
## <a name="sql-server-mixed-mode-not-supported"></a><span data-ttu-id="f8199-108">En mode mixte SQL Server non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f8199-108">SQL Server mixed mode not supported</span></span>  
<span data-ttu-id="f8199-109">Le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ne prend pas en charge SQL Server en mode mixte.</span><span class="sxs-lookup"><span data-stu-id="f8199-109">The [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] does not support SQL Server in mixed mode.</span></span>  
  
## <a name="repair-does-not-work-from-uninstallchange"></a><span data-ttu-id="f8199-110">La réparation ne fonctionne pas de désinstaller/modifier</span><span class="sxs-lookup"><span data-stu-id="f8199-110">Repair does not work from uninstall/change</span></span>  
<span data-ttu-id="f8199-111">Si le contrôle d’accès utilisateur (UAC) est activé et que vous essayez de réparer votre installation en utilisant le panneau de configuration, la réparation échoue.</span><span class="sxs-lookup"><span data-stu-id="f8199-111">If user access control (UAC) is enabled, and you try to repair your installation using the control panel, the repair fails.</span></span> 

<span data-ttu-id="f8199-112">Microsoft recommande que vous conservez le compte d’utilisateur activé.</span><span class="sxs-lookup"><span data-stu-id="f8199-112">Microsoft recommends you keep UAC enabled.</span></span>

 <span data-ttu-id="f8199-113">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="f8199-113">**Resolution**</span></span>  
  
 <span data-ttu-id="f8199-114">Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup.exe, puis sélectionnez **réparation**.</span><span class="sxs-lookup"><span data-stu-id="f8199-114">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup.exe, and then select **Repair**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8199-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8199-115">See Also</span></span>  
[<span data-ttu-id="f8199-116">Installer ou mettre à niveau de Microsoft BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="f8199-116">Install or upgrade Microsoft BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)