---
title: "Déploiement Limitations4 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, deployment limitations
- deployment, limitations
ms.assetid: 1312627e-9de2-461e-a8c4-66a9d41bb714
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2d8e33c7274ab0f95c6d7fff1bf9746ac86e420
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="9663a-102">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="9663a-102">Deployment Limitations</span></span>
<span data-ttu-id="9663a-103">Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoile (*) dans le fichier de liaison exporté par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion dans le même format.</span><span class="sxs-lookup"><span data-stu-id="9663a-103">The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span> <span data-ttu-id="9663a-104">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="9663a-104">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span>  
  
 <span data-ttu-id="9663a-105">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9663a-105">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="9663a-106">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="9663a-106">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="9663a-107">La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.</span><span class="sxs-lookup"><span data-stu-id="9663a-107">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span>  
  
 <span data-ttu-id="9663a-108">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="9663a-108">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="9663a-109">Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.</span><span class="sxs-lookup"><span data-stu-id="9663a-109">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9663a-110">Lors de l'importation d'un fichier .msi dans une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contenant les informations de liaison pour un adaptateur d'entreprise, un message d'erreur relatif à l'importation peut s'afficher.</span><span class="sxs-lookup"><span data-stu-id="9663a-110">When importing an .msi file in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="9663a-111">Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://go.microsoft.com/fwlink/?LinkId=196087](http://go.microsoft.com/fwlink/?LinkId=196087).</span><span class="sxs-lookup"><span data-stu-id="9663a-111">A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkId=196087](http://go.microsoft.com/fwlink/?LinkId=196087).</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="9663a-112">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="9663a-112">Password Limitation Workaround</span></span>  
 <span data-ttu-id="9663a-113">Pour contourner la limitation de mot de passe, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9663a-113">To work around the password limitation, you can do the following.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="9663a-114">Pour contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="9663a-114">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="9663a-115">Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="9663a-115">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="9663a-116">Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.</span><span class="sxs-lookup"><span data-stu-id="9663a-116">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="9663a-117">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="9663a-117">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9663a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9663a-118">See Also</span></span>  
 [<span data-ttu-id="9663a-119">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="9663a-119">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies3.md)