---
title: "Déploiement Limitations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, limitations
ms.assetid: a984ccce-37b2-4738-b652-7232a18e0510
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e65fb1c1a1211865b07c3abb987f0a1d31fbfd69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="56ba6-102">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="56ba6-102">Deployment Limitations</span></span>
<span data-ttu-id="56ba6-103">Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoiles (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par BizTalk Server et la transmet au composant de gestion dans le même format.</span><span class="sxs-lookup"><span data-stu-id="56ba6-103">The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format.</span></span> <span data-ttu-id="56ba6-104">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="56ba6-104">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="56ba6-105">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="56ba6-105">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
 <span data-ttu-id="56ba6-106">Il s'agit d'une limitation connue.</span><span class="sxs-lookup"><span data-stu-id="56ba6-106">This is a known limitation.</span></span> <span data-ttu-id="56ba6-107">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="56ba6-107">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="56ba6-108">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="56ba6-108">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="56ba6-109">Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport.</span><span class="sxs-lookup"><span data-stu-id="56ba6-109">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="56ba6-110">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="56ba6-110">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="56ba6-111">Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison une fois l’opération d’importation terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="56ba6-111">In this case, you must delete the passwords from the binding file after the import operation successfully finishes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56ba6-112">Lors de l'importation d'un fichier .msi dans l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contenant les informations de liaison pour un adaptateur d'entreprise, un message d'erreur relatif à l'importation peut s'afficher.</span><span class="sxs-lookup"><span data-stu-id="56ba6-112">When importing an .msi file in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="56ba6-113">Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).</span><span class="sxs-lookup"><span data-stu-id="56ba6-113">A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="56ba6-114">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="56ba6-114">Password Limitation Workaround</span></span>  
 <span data-ttu-id="56ba6-115">Pour contourner cette limitation de mot de passe, vous pouvez suivre l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="56ba6-115">To work around this password limitation, you can use one of the following methods:</span></span>  
  
-   <span data-ttu-id="56ba6-116">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="56ba6-116">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="56ba6-117">Cette opération n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="56ba6-117">This is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="56ba6-118">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="56ba6-118">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="56ba6-119">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="56ba6-119">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56ba6-120">Cette solution de contournement ne peut être utilisée que si Visual Studio est installé sur l'ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="56ba6-120">This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.</span></span>  
  
-   <span data-ttu-id="56ba6-121">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="56ba6-121">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ba6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56ba6-122">See Also</span></span>  
 [<span data-ttu-id="56ba6-123">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="56ba6-123">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies2.md)