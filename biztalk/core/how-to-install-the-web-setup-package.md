---
title: "Comment installer le Package d’installation Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, deploying
- Web services, installing
ms.assetid: c6b38a2f-ad07-4ccd-b267-9e3510df88c3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21fbacd76598a3a86cfa70b4761bc74420afe561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-web-setup-package"></a><span data-ttu-id="b78f7-102">Comment installer le Package d’installation Web</span><span class="sxs-lookup"><span data-stu-id="b78f7-102">How to Install the Web Setup Package</span></span>
<span data-ttu-id="b78f7-103">Le contenu du dossier de distribution permet d'installer le service Web sur un ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="b78f7-103">Use the contents of the distribution folder to setup the Web service on a destination computer.</span></span>  
  
### <a name="to-install-the-web-setup-package"></a><span data-ttu-id="b78f7-104">Pour installer le package d'installation Web</span><span class="sxs-lookup"><span data-stu-id="b78f7-104">To install the Web setup package</span></span>  
  
1.  <span data-ttu-id="b78f7-105">Copiez le dossier de distribution sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="b78f7-105">Copy the distribution folder onto the destination computer.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b78f7-106">Le composant d'exécution BizTalk Server doit être installé sur l'ordinateur de destination et les assemblys BizTalk appropriés doivent être déployés et installés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b78f7-106">The destination computer must have the BizTalk Server runtime installed and the necessary BizTalk assemblies deployed and installed in the global assembly cache.</span></span>  
  
2.  <span data-ttu-id="b78f7-107">Exécutez le. Fichier MSI pour installer le service Web et suivez l’Assistant Installation vous invite à entrer.</span><span class="sxs-lookup"><span data-stu-id="b78f7-107">Run the .MSI file to install the Web service and follow the setup wizard prompts.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b78f7-108">Supprimez le suffixe « _Setup » lorsque l’Assistant vous invite à entrer le répertoire virtuel. Supprimer le suffixe garantit que les adresses d’emplacement de réception correspondent aux fichiers .asmx de service Web.</span><span class="sxs-lookup"><span data-stu-id="b78f7-108">Remove the "_Setup" suffix when the wizard prompts you for the virtual directory.Removing the suffix ensures that the receive location addresses match the Web service .asmx files.</span></span>  
  
3.  <span data-ttu-id="b78f7-109">Vérifiez que les paramètres de sécurité du répertoire virtuel sont appropriés pour l'autorisation.</span><span class="sxs-lookup"><span data-stu-id="b78f7-109">Verify that the security settings for the virtual directory are correct for authorization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78f7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b78f7-110">See Also</span></span>  
 [<span data-ttu-id="b78f7-111">Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b78f7-111">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)