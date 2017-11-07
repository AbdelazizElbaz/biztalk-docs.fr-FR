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
# <a name="deployment-limitations"></a>Limitations concernant le déploiement

## <a name="overview"></a>Vue d'ensemble
Le mot de passe de l'adaptateur de transport est stocké sous forme d'astérisques (******) dans le fichier de liaison exporté par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion au même format.  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison à l’issue de l’opération d’importation.  
  

## <a name="password-limitation-workaround"></a>Contournement de la limitation de mot de passe  
 Pour contourner cette limitation de mot de passe, vous pouvez suivre l'une des méthodes suivantes :  
  
-   Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.  
  
    > [!CAUTION]
    >  Cette pratique n'est pas recommandée pour des raisons de sécurité.  
  
-   Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.  
  
    > [!NOTE]
    >  Cette solution de contournement ne peut être utilisée que si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est installé sur l'ordinateur cible ou en développant un outil personnalisé.  
  
 -ou-  
  
-   Utilisez l'authentification unique de l'entreprise (SSO) plutôt que des mots de passe.  
  
     L'utilisation de l'option SSO nécessite l'importation d'un fichier de liaison.  
  
 Vérifiez le système logique et le transmettre et recevoir des services.  
  
## <a name="see-also"></a>Voir aussi  
[Importer les liaisons et limitations](../core/deploying-biztalk-adapter-for-peoplesoft-enterprise.md)