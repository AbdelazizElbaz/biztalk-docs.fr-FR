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
# <a name="deployment-limitations"></a>Limitations concernant le déploiement
Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoile (*) dans le fichier de liaison exporté par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion dans le même format. Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.  
  
 Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.  
  
> [!NOTE]
>  Lors de l'importation d'un fichier .msi dans une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contenant les informations de liaison pour un adaptateur d'entreprise, un message d'erreur relatif à l'importation peut s'afficher. Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://go.microsoft.com/fwlink/?LinkId=196087](http://go.microsoft.com/fwlink/?LinkId=196087).  
  
## <a name="password-limitation-workaround"></a>Contournement de la limitation de mot de passe  
 Pour contourner la limitation de mot de passe, procédez comme suit :  
  
#### <a name="to-work-around-the-password-limitation"></a>Pour contourner la limitation de mot de passe  
  
1.  Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe. Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.  
  
2.  Vérifiez le système logique et les services de transmission et de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies3.md)