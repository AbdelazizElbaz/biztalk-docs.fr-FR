---
title: "Déploiement Limitations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deployment, limitations
- passwords, adapter limitations
ms.assetid: 9db2ca70-5db2-4b14-a898-13049737c188
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05fa9704823bd7e9df9f0bc7d4516719a8a490e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="47bb1-102">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="47bb1-102">Deployment Limitations</span></span>
<span data-ttu-id="47bb1-103">Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par l’Assistant Déploiement BizTalk et est transmis à la gestion composant dans le même format.</span><span class="sxs-lookup"><span data-stu-id="47bb1-103">The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format.</span></span> <span data-ttu-id="47bb1-104">Avant d'importer le fichier de liaison, vous devez le modifier en remplaçant les astérisques par des valeurs alphanumériques aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="47bb1-104">Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password).</span></span> <span data-ttu-id="47bb1-105">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="47bb1-105">Then enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
 <span data-ttu-id="47bb1-106">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="47bb1-106">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="47bb1-107">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="47bb1-107">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="47bb1-108">La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.</span><span class="sxs-lookup"><span data-stu-id="47bb1-108">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="47bb1-109">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="47bb1-109">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="47bb1-110">Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.</span><span class="sxs-lookup"><span data-stu-id="47bb1-110">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47bb1-111">Lors de l’importation d’un fichier .msi dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application contenant des informations de liaison pour un adaptateur d’entreprise, vous pouvez recevoir un message d’erreur d’importation.</span><span class="sxs-lookup"><span data-stu-id="47bb1-111">When importing an .msi file into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="47bb1-112">Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).</span><span class="sxs-lookup"><span data-stu-id="47bb1-112">A supported hotfix is available from Microsoft along with a full description of the error at [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="47bb1-113">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="47bb1-113">Password Limitation Workaround</span></span>  
 <span data-ttu-id="47bb1-114">Utilisez l'une des solutions suivantes pour contourner la limitation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="47bb1-114">Use one of the following as a work-around for the password limitation.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="47bb1-115">Pour contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="47bb1-115">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="47bb1-116">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="47bb1-116">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="47bb1-117">Cette opération n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="47bb1-117">This is not recommended for security reasons.</span></span>  
  
2.  <span data-ttu-id="47bb1-118">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="47bb1-118">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="47bb1-119">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="47bb1-119">Enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="47bb1-120">Cette solution de contournement peut être utilisée uniquement si Microsoft Visual Studio est installé sur l’ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="47bb1-120">This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.</span></span>  
  
 <span data-ttu-id="47bb1-121">**- OU -**</span><span class="sxs-lookup"><span data-stu-id="47bb1-121">**-OR-**</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="47bb1-122">Pour contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="47bb1-122">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="47bb1-123">Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="47bb1-123">Use Enterprise Single Sign-On instead of using passwords.</span></span>  
  
     <span data-ttu-id="47bb1-124">Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.</span><span class="sxs-lookup"><span data-stu-id="47bb1-124">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="47bb1-125">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="47bb1-125">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47bb1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47bb1-126">See Also</span></span>  
 <span data-ttu-id="47bb1-127">[Comment définir les propriétés de JD Edwards OneWorld Transport](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span><span class="sxs-lookup"><span data-stu-id="47bb1-127">[How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span></span>  
 [<span data-ttu-id="47bb1-128">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="47bb1-128">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies4.md)