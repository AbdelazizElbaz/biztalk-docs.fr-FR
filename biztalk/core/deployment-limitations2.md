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
# <a name="deployment-limitations"></a>Limitations concernant le déploiement
Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par l’Assistant Déploiement BizTalk et est transmis à la gestion composant dans le même format. Avant d'importer le fichier de liaison, vous devez le modifier en remplaçant les astérisques par des valeurs alphanumériques aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.  
  

## <a name="password-limitation-workaround"></a>Contournement de la limitation de mot de passe  
 Utilisez l'une des solutions suivantes pour contourner la limitation de mot de passe.  
  
#### <a name="to-work-around-the-password-limitation"></a>Pour contourner la limitation de mot de passe  
  
1.  Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.  
  
    > [!CAUTION]
    >  Cette opération n'est pas recommandée pour des raisons de sécurité.  
  
2.  Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.  
  
    > [!NOTE]
    >  Cette solution de contournement peut être utilisée uniquement si Microsoft Visual Studio est installé sur l’ordinateur cible ou en développant un outil personnalisé.  
  
 **- OU -**  
  
#### <a name="to-work-around-the-password-limitation"></a>Pour contourner la limitation de mot de passe  
  
1.  Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe.  
  
     Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.  
  
2.  Vérifiez le système logique et les services de transmission et de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [Importer le JD Edwards OneWorld application](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)