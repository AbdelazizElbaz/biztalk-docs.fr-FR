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
# <a name="deployment-limitations"></a>Limitations concernant le déploiement
Le mot de passe de l'adaptateur de transport est stocké sous forme d'astérisques (******) dans le fichier de liaison exporté par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion au même format.  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison à l’issue de l’opération d’importation.  
  
> [!NOTE]
>  Lors de l'importation d'un fichier .msi dans une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contenant les informations de liaison pour un adaptateur d'entreprise, un message d'erreur relatif à l'importation peut s'afficher. Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).  
  
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
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies5.md)