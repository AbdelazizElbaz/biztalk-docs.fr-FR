---
title: "Comment configurer le répertoire virtuel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directory, configuring
- configuring virtual directory
- applications, verifying for users
- verifying applications for users
ms.assetid: 3da16524-8238-426a-88f8-434be5992e13
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f00c5f75062ffd084cd19f23bfa66768d3d67ca5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-virtual-directory"></a><span data-ttu-id="6d890-102">Comment configurer le répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="6d890-102">How to Configure the Virtual Directory</span></span>
<span data-ttu-id="6d890-103">Cette rubrique décrit les procédures de configuration du répertoire virtuel et de vérification de l'application pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d890-103">This topic describes the procedures for configuring the virtual directory and verifying the application for a user.</span></span>  
  
### <a name="to-configure-the-virtual-directory"></a><span data-ttu-id="6d890-104">Pour configurer le répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="6d890-104">To configure the virtual directory</span></span>  
  
1.  <span data-ttu-id="6d890-105">Sur le lecteur système (%systemdrive%), créez un dossier à configurer en tant que répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="6d890-105">On the %systemdrive%, create a folder to be configured as a virtual directory.</span></span>  
  
2.  <span data-ttu-id="6d890-106">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="6d890-106">Click **Start**, point to **Programs**, click **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span>  
  
3.  <span data-ttu-id="6d890-107">Développez  **\<nom du serveur\>**  , puis **Sites**.</span><span class="sxs-lookup"><span data-stu-id="6d890-107">Expand **\<server name\>** and then expand **Sites**.</span></span>  
  
4.  <span data-ttu-id="6d890-108">Avec le bouton droit **Site Web par défaut** et cliquez sur **ajouter un répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6d890-108">Right-click **Default Web Site** and click **Add Virtual Directory**.</span></span>  
  
5.  <span data-ttu-id="6d890-109">Dans le **ajouter un répertoire virtuel** boîte de dialogue, tapez l’alias.</span><span class="sxs-lookup"><span data-stu-id="6d890-109">In the **Add Virtual Directory** dialog box, type the alias.</span></span>  
  
6.  <span data-ttu-id="6d890-110">Tapez le chemin d'accès au dossier créé à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="6d890-110">Type the path of the folder created in step 1.</span></span> <span data-ttu-id="6d890-111">Sinon, cliquez sur **(...)**  pour accéder à l’emplacement du dossier.</span><span class="sxs-lookup"><span data-stu-id="6d890-111">Alternatively, click **(…)** to browse to the folder location.</span></span>  
  
7.  <span data-ttu-id="6d890-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6d890-112">Click **OK**.</span></span> <span data-ttu-id="6d890-113">Le dossier s’affiche sous le **Site Web par défaut** dossier.</span><span class="sxs-lookup"><span data-stu-id="6d890-113">The folder is displayed under the **Default Web Site** folder.</span></span>  
  
8.  <span data-ttu-id="6d890-114">Cliquez avec le bouton droit et cliquez sur **convertir en Application**.</span><span class="sxs-lookup"><span data-stu-id="6d890-114">Right-click the folder and click **Convert to Application**.</span></span>  
  
9. <span data-ttu-id="6d890-115">Dans le **ajouter une Application** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6d890-115">In the **Add Application** dialog box, click **OK**.</span></span> <span data-ttu-id="6d890-116">Le dossier est converti en application (l'icône de dossier devient une icône de site Web).</span><span class="sxs-lookup"><span data-stu-id="6d890-116">The folder is converted to an application (you can see the change in the icon – from a folder icon to the Web site icon).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d890-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d890-117">See Also</span></span>  
 [<span data-ttu-id="6d890-118">Sécuriser l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="6d890-118">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)