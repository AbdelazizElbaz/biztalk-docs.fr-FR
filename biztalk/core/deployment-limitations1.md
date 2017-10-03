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
# <a name="deployment-limitations"></a>Limitations concernant le déploiement
Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoiles (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par BizTalk Server et la transmet au composant de gestion dans le même format. Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.  
  
 Il s'agit d'une limitation connue. Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison une fois l’opération d’importation terminée avec succès.  
  
> [!NOTE]
>  Lors de l'importation d'un fichier .msi dans l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contenant les informations de liaison pour un adaptateur d'entreprise, un message d'erreur relatif à l'importation peut s'afficher. Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).  
  
## <a name="password-limitation-workaround"></a>Contournement de la limitation de mot de passe  
 Pour contourner cette limitation de mot de passe, vous pouvez suivre l'une des méthodes suivantes :  
  
-   Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.  
  
> [!CAUTION]
>  Cette opération n'est pas recommandée pour des raisons de sécurité.  
  
-   Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.  
  
> [!NOTE]
>  Cette solution de contournement ne peut être utilisée que si Visual Studio est installé sur l'ordinateur cible ou en développant un outil personnalisé.  
  
-   Vérifiez le système logique et les services de transmission et de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies2.md)