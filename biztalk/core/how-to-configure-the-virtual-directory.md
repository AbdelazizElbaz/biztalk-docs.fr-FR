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
ms.openlocfilehash: 1b1461ac2ea0ef9cfee71965fc2cc800d617d1d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-virtual-directory"></a><span data-ttu-id="08bfc-102">Comment configurer le répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="08bfc-102">How to Configure the Virtual Directory</span></span>
<span data-ttu-id="08bfc-103">Cette rubrique décrit les procédures de configuration du répertoire virtuel et de vérification de l'application pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="08bfc-103">This topic describes the procedures for configuring the virtual directory and verifying the application for a user.</span></span>  
  
### <a name="to-configure-the-virtual-directory"></a><span data-ttu-id="08bfc-104">Pour configurer le répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="08bfc-104">To configure the virtual directory</span></span>  
  
1.  <span data-ttu-id="08bfc-105">Sur le lecteur système (%systemdrive%), créez un dossier à configurer en tant que répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="08bfc-105">On the %systemdrive%, create a folder to be configured as a virtual directory.</span></span>  
  
2.  <span data-ttu-id="08bfc-106">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="08bfc-106">Click **Start**, point to **Programs**, click **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span>  
  
3.  <span data-ttu-id="08bfc-107">Développez  **\<nom du serveur >** , puis **Sites**.</span><span class="sxs-lookup"><span data-stu-id="08bfc-107">Expand **\<server name>** and then expand **Sites**.</span></span>  
  
4.  <span data-ttu-id="08bfc-108">Avec le bouton droit **Site Web par défaut** et cliquez sur **ajouter un répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="08bfc-108">Right-click **Default Web Site** and click **Add Virtual Directory**.</span></span>  
  
5.  <span data-ttu-id="08bfc-109">Dans le **ajouter un répertoire virtuel** boîte de dialogue, tapez l’alias.</span><span class="sxs-lookup"><span data-stu-id="08bfc-109">In the **Add Virtual Directory** dialog box, type the alias.</span></span>  
  
6.  <span data-ttu-id="08bfc-110">Tapez le chemin d'accès au dossier créé à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="08bfc-110">Type the path of the folder created in step 1.</span></span> <span data-ttu-id="08bfc-111">Sinon, cliquez sur **(...)**  pour accéder à l’emplacement du dossier.</span><span class="sxs-lookup"><span data-stu-id="08bfc-111">Alternatively, click **(…)** to browse to the folder location.</span></span>  
  
7.  <span data-ttu-id="08bfc-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="08bfc-112">Click **OK**.</span></span> <span data-ttu-id="08bfc-113">Le dossier s’affiche sous le **Site Web par défaut** dossier.</span><span class="sxs-lookup"><span data-stu-id="08bfc-113">The folder is displayed under the **Default Web Site** folder.</span></span>  
  
8.  <span data-ttu-id="08bfc-114">Cliquez avec le bouton droit et cliquez sur **convertir en Application**.</span><span class="sxs-lookup"><span data-stu-id="08bfc-114">Right-click the folder and click **Convert to Application**.</span></span>  
  
9. <span data-ttu-id="08bfc-115">Dans le **ajouter une Application** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="08bfc-115">In the **Add Application** dialog box, click **OK**.</span></span> <span data-ttu-id="08bfc-116">Le dossier est converti en application (l'icône de dossier devient une icône de site Web).</span><span class="sxs-lookup"><span data-stu-id="08bfc-116">The folder is converted to an application (you can see the change in the icon – from a folder icon to the Web site icon).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08bfc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08bfc-117">See Also</span></span>  
 [<span data-ttu-id="08bfc-118">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="08bfc-118">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)