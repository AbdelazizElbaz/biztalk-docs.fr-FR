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
# <a name="deployment-limitations"></a>Limitations concernant le déploiement
Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par l’Assistant Déploiement BizTalk et est transmis à la gestion composant dans le même format. Avant d'importer le fichier de liaison, vous devez le modifier en remplaçant les astérisques par des valeurs alphanumériques aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.  
  
> [!NOTE]
>  Lors de l’importation d’un fichier .msi dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application contenant des informations de liaison pour un adaptateur d’entreprise, vous pouvez recevoir un message d’erreur d’importation. Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).  
  
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
 [Comment définir les propriétés de JD Edwards OneWorld Transport](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)   
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies4.md)