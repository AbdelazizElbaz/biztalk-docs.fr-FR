---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: acc8560096423eb69b7cad8d9e6264707ae9a636
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="4d9a8-101">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="4d9a8-101">Deployment Limitations</span></span>

## <a name="overview"></a><span data-ttu-id="4d9a8-102">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="4d9a8-102">Overview</span></span>
<span data-ttu-id="4d9a8-103">Le mot de passe de l'adaptateur de transport est stocké sous forme d'astérisques (******) dans le fichier de liaison exporté par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion au même format.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-103">The Transport Adapter password is stored as stars (******) in the binding file that is exported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span>  
  
 <span data-ttu-id="4d9a8-104">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-104">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="4d9a8-105">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-105">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="4d9a8-106">Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-106">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="4d9a8-107">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-107">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="4d9a8-108">Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison à l’issue de l’opération d’importation.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-108">In this case, you must delete the passwords from the binding file after the import operation finishes.</span></span>  
  

## <a name="password-limitation-workaround"></a><span data-ttu-id="4d9a8-109">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="4d9a8-109">Password Limitation Workaround</span></span>  
 <span data-ttu-id="4d9a8-110">Pour contourner cette limitation de mot de passe, vous pouvez suivre l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d9a8-110">To work around this password limitation, you can use one of the following methods:</span></span>  
  
-   <span data-ttu-id="4d9a8-111">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-111">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="4d9a8-112">Cette pratique n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-112">This practice is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="4d9a8-113">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="4d9a8-113">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="4d9a8-114">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-114">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d9a8-115">Cette solution de contournement ne peut être utilisée que si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est installé sur l'ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-115">This work-around can be used only if Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is installed on the target computer, or if you develop a custom tool.</span></span>  
  
 <span data-ttu-id="4d9a8-116">-ou-</span><span class="sxs-lookup"><span data-stu-id="4d9a8-116">-or-</span></span>  
  
-   <span data-ttu-id="4d9a8-117">Utilisez l'authentification unique de l'entreprise (SSO) plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-117">Use Enterprise Single Sign-On (SSO) instead of using passwords.</span></span>  
  
     <span data-ttu-id="4d9a8-118">L'utilisation de l'option SSO nécessite l'importation d'un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-118">Using the SSO option requires an import of the binding file.</span></span>  
  
 <span data-ttu-id="4d9a8-119">Vérifiez le système logique et le transmettre et recevoir des services.</span><span class="sxs-lookup"><span data-stu-id="4d9a8-119">Verify the logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d9a8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d9a8-120">See Also</span></span>  
[<span data-ttu-id="4d9a8-121">Importer les liaisons et limitations</span><span class="sxs-lookup"><span data-stu-id="4d9a8-121">Import bindings & limitations</span></span>](../core/deploying-biztalk-adapter-for-peoplesoft-enterprise.md)