---
title: "Déploiement Limitations3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, deployment limitations
- deployment, password limitations
- transport adapter password
ms.assetid: 79cd330f-ecc5-430e-9d79-608593d873cb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae0d01947e0769189c269a1853e7fda0e11cedb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="8c682-102">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="8c682-102">Deployment Limitations</span></span>
<span data-ttu-id="8c682-103">Le mot de passe de l'adaptateur de transport est stocké sous forme d'astérisques (******) dans le fichier de liaison exporté par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion au même format.</span><span class="sxs-lookup"><span data-stu-id="8c682-103">The Transport Adapter password is stored as stars (******) in the binding file that is exported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span>  
  
 <span data-ttu-id="8c682-104">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="8c682-104">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="8c682-105">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="8c682-105">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="8c682-106">Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport.</span><span class="sxs-lookup"><span data-stu-id="8c682-106">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="8c682-107">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="8c682-107">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="8c682-108">Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison à l’issue de l’opération d’importation.</span><span class="sxs-lookup"><span data-stu-id="8c682-108">In this case, you must delete the passwords from the binding file after the import operation finishes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c682-109">Lors de l'importation d'un fichier .msi dans une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contenant les informations de liaison pour un adaptateur d'entreprise, un message d'erreur relatif à l'importation peut s'afficher.</span><span class="sxs-lookup"><span data-stu-id="8c682-109">When importing an .msi file in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="8c682-110">Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).</span><span class="sxs-lookup"><span data-stu-id="8c682-110">A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="8c682-111">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8c682-111">Password Limitation Workaround</span></span>  
 <span data-ttu-id="8c682-112">Pour contourner cette limitation de mot de passe, vous pouvez suivre l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c682-112">To work around this password limitation, you can use one of the following methods:</span></span>  
  
-   <span data-ttu-id="8c682-113">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="8c682-113">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="8c682-114">Cette pratique n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8c682-114">This practice is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="8c682-115">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="8c682-115">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="8c682-116">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="8c682-116">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c682-117">Cette solution de contournement ne peut être utilisée que si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est installé sur l'ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8c682-117">This work-around can be used only if Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is installed on the target computer, or if you develop a custom tool.</span></span>  
  
 <span data-ttu-id="8c682-118">-ou-</span><span class="sxs-lookup"><span data-stu-id="8c682-118">-or-</span></span>  
  
-   <span data-ttu-id="8c682-119">Utilisez l'authentification unique de l'entreprise (SSO) plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="8c682-119">Use Enterprise Single Sign-On (SSO) instead of using passwords.</span></span>  
  
     <span data-ttu-id="8c682-120">L'utilisation de l'option SSO nécessite l'importation d'un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="8c682-120">Using the SSO option requires an import of the binding file.</span></span>  
  
 <span data-ttu-id="8c682-121">Vérifiez le système logique et le transmettre et recevoir des services.</span><span class="sxs-lookup"><span data-stu-id="8c682-121">Verify the logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c682-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c682-122">See Also</span></span>  
 [<span data-ttu-id="8c682-123">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="8c682-123">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies5.md)