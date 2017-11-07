---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 64f202316e59040a77cb04da99857e8539a184ac
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="f55d8-101">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="f55d8-101">Deployment Limitations</span></span>
<span data-ttu-id="f55d8-102">Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par l’Assistant Déploiement BizTalk et est transmis à la gestion composant dans le même format.</span><span class="sxs-lookup"><span data-stu-id="f55d8-102">The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format.</span></span> <span data-ttu-id="f55d8-103">Avant d'importer le fichier de liaison, vous devez le modifier en remplaçant les astérisques par des valeurs alphanumériques aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="f55d8-103">Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password).</span></span> <span data-ttu-id="f55d8-104">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="f55d8-104">Then enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
 <span data-ttu-id="f55d8-105">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f55d8-105">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="f55d8-106">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="f55d8-106">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="f55d8-107">La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.</span><span class="sxs-lookup"><span data-stu-id="f55d8-107">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="f55d8-108">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="f55d8-108">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="f55d8-109">Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.</span><span class="sxs-lookup"><span data-stu-id="f55d8-109">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  

## <a name="password-limitation-workaround"></a><span data-ttu-id="f55d8-110">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="f55d8-110">Password Limitation Workaround</span></span>  
 <span data-ttu-id="f55d8-111">Utilisez l'une des solutions suivantes pour contourner la limitation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f55d8-111">Use one of the following as a work-around for the password limitation.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="f55d8-112">Pour contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="f55d8-112">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="f55d8-113">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="f55d8-113">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="f55d8-114">Cette opération n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f55d8-114">This is not recommended for security reasons.</span></span>  
  
2.  <span data-ttu-id="f55d8-115">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="f55d8-115">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="f55d8-116">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="f55d8-116">Enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f55d8-117">Cette solution de contournement peut être utilisée uniquement si Microsoft Visual Studio est installé sur l’ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f55d8-117">This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.</span></span>  
  
 <span data-ttu-id="f55d8-118">**- OU -**</span><span class="sxs-lookup"><span data-stu-id="f55d8-118">**-OR-**</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="f55d8-119">Pour contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="f55d8-119">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="f55d8-120">Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="f55d8-120">Use Enterprise Single Sign-On instead of using passwords.</span></span>  
  
     <span data-ttu-id="f55d8-121">Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.</span><span class="sxs-lookup"><span data-stu-id="f55d8-121">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="f55d8-122">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="f55d8-122">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f55d8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f55d8-123">See Also</span></span>  
 <span data-ttu-id="f55d8-124">[Ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="f55d8-124">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="f55d8-125">Importer le JD Edwards OneWorld application</span><span class="sxs-lookup"><span data-stu-id="f55d8-125">Import the JD Edwards OneWorld app</span></span>](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)