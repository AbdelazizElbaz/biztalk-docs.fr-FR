---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 847e66c189cb8fc14014691f95d78b6eec4b45dc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="87fef-101">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="87fef-101">Deployment Limitations</span></span>
<span data-ttu-id="87fef-102">Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoile (*) dans le fichier de liaison exporté par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion dans le même format.</span><span class="sxs-lookup"><span data-stu-id="87fef-102">The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span> <span data-ttu-id="87fef-103">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="87fef-103">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span>  
  
 <span data-ttu-id="87fef-104">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="87fef-104">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="87fef-105">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="87fef-105">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="87fef-106">La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.</span><span class="sxs-lookup"><span data-stu-id="87fef-106">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span>  
  
 <span data-ttu-id="87fef-107">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="87fef-107">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="87fef-108">Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.</span><span class="sxs-lookup"><span data-stu-id="87fef-108">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="87fef-109">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="87fef-109">Password Limitation Workaround</span></span>  
 <span data-ttu-id="87fef-110">Pour contourner la limitation de mot de passe, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="87fef-110">To work around the password limitation, you can do the following.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="87fef-111">Pour contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="87fef-111">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="87fef-112">Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="87fef-112">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="87fef-113">Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.</span><span class="sxs-lookup"><span data-stu-id="87fef-113">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="87fef-114">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="87fef-114">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fef-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87fef-115">See Also</span></span>  
 [<span data-ttu-id="87fef-116">Importer le JD Edwards EnterpriseOne application</span><span class="sxs-lookup"><span data-stu-id="87fef-116">Import the JD Edwards EnterpriseOne app</span></span>](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)