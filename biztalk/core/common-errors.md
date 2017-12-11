---
title: Les erreurs courantes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fe48a8e-def0-4a00-aa7f-9a49ae555351
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b882c44e69489114a2dd8084df71d6414df0cb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="common-errors"></a>Erreurs fréquentes
Cette rubrique répertorie les messages d'erreur courants que vous pouvez rencontrer lors de la création de mappages à l'aide du Mappeur BizTalk.  
  
## <a name="you-receive-error-event-id-324-when-parsing-dates"></a>L'ID d'événement d'erreur 324 s'affiche lors de l'analyse de dates  
  
### <a name="problem"></a>Problème  
 Lorsque vous utilisez la base de données **extracteur de valeur** fonctoid dans un mappage pour extraire un champ de date, votre document peut échouer la validation par rapport à la définition de document sortant. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]le journal des événements peut connecter une erreur de validation similaire au suivant :  
  
 Source d’événement : BizTalk Server  
  
 Catégorie d’événement : Le traitement des documents  
  
 ID d’événement : 324  
  
 Description :  
  
 Une erreur s'est produite dans BizTalk Server.  
  
 Détails :  
  
 -----------------------------\-  
  
 Le document XML n’a pas pour la raison suivante : erreur d’analyse de ' 10/12/1995 ' comme type de données de date.  
  
 ID de la file d’attente suspendue : « {A1127909-CA36-4359-B672-7CBA8B60BDAF} »  
  
### <a name="cause"></a>Cause  
 Le format de date (tel que renvoyé par la source de données) n'est pas conforme au format ISO 8601, le format requis par XML.  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, effectuez l’une des opérations suivantes :  
  
-   Modifiez la définition du document sortant afin d'utiliser un type de données chaîne au lieu d'un type de données date.  
  
-   Créer un personnalisé [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsVBNoVersion](../includes/btsvbnoversion-md.md)] **Script** fonctoid qui convertira la sortie de la base de données **extracteur de valeur** fonctoid dans le format ISO 8601.  
  
 Pour plus d’informations, consultez l’article [278737](http://support.microsoft.com/kb/278737/en-us).  
  
## <a name="you-receive-internal-compiler-error-0xc0000005-at-address-53624fd6-when-compiling-the-maps"></a>L'erreur interne du compilateur (0xc0000005 à l'adresse 53624FD6) s'affiche lors de la compilation des mappages  
  
### <a name="problem"></a>Problème  
 Lors de la compilation d'un seul projet BizTalk comprenant des schémas, mappages ou orchestrations de grande taille, le compilateur peut générer une erreur similaire à ce qui suit :  
  
 Erreur interne du compilateur (0xc0000005 à l’adresse 53624FD6) : en est probablement 'CODEGEN'.  
  
### <a name="cause"></a>Cause  
 Le compilateur [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] limite à 16 Mo la taille totale de l'ensemble des chaînes d'un seul projet. Lors de la compilation des projets BizTalk, le compilateur sérialise les schémas, les mappages et les orchestrations pour créer les assemblys, ce qui accroît la taille totale des chaînes parfois au-delà de la limite autorisée.  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, vous pouvez diviser les schémas ou les mappages en plusieurs projets BizTalk.  
  
## <a name="you-receive-errors-about-the-type-name-of-a-biztalk-artifact"></a>Des erreurs concernant le nom du type d'un artefact BizTalk s'affichent  
  
### <a name="problem"></a>Problème  
 Dans un projet BizTalk, créer un mappage avec le nom de fichier **System.btm** ou **Microsoft.btm**. Lors de la création du projet, le Mappeur BizTalk génère une erreur similaire à ce qui suit :  
  
-   « Le nom du type 'SerializableAttribute' n'existe pas... »  
  
-   « Le nom du type 'NonSerializableAttribute' n'existe pas... »  
  
-   « Le nom du type 'SerializableAttributeAttribute' n'existe pas... »  
  
-   « Le nom du type 'XLANs' n'existe pas... »  
  
### <a name="cause"></a>Cause  
 Le **nom de Type** dans les **propriétés** grille ne devrait pas les espaces de noms .NET réservé, tel que **système**, **Microsoft**, etc.  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, suivez l'une des solutions suivantes :  
  
-   Modifiez le nom du mappage par une chaîne n'étant pas un mot réservé .NET. Par défaut, le système de projet BizTalk crée le **nom de Type** à partir du nom de l’artefact correspondant.  
  
     Pour, par exemple : création d’un mappage avec le nom **Map1.btm** définit le **nom de Type** valeur de propriété à **Map1**. Toutefois, renommer un BizTalk existant artefact ne modifie pas le **nom de Type**.  
  
-   Vérifiez que le nom de fichier de chaque artefact du projet BizTalk ne correspond à aucun espace de noms réservé .NET.  
  
## <a name="you-receive-errors-about-the-file-name-of-a-biztalk-artifact"></a>Des erreurs concernant le nom de fichier d'un artefact BizTalk s'affichent  
  
### <a name="problem"></a>Problème  
 Lors de la création d'un projet BizTalk, le Mappeur BizTalk génère une erreur similaire à ce qui suit :  
  
-   « Le fichier \<nom de fichier\> a des valeurs en double pour les propriétés du nom de type et espace de noms. »  
  
-   « L’espace de noms \<nom\> contient déjà une définition pour '_'. »  
  
### <a name="cause"></a>Cause  
 Dans le projet BizTalk, vérifiez les éléments suivants :  
  
-   Plusieurs artefacts possèdent le même nom de fichier. Pour, par exemple, **Map1.xsd** et**Map1.btm**.  
  
-   Le nom de fichier comprend uniquement des caractères spéciaux (**~**, **!**,  **@** , etc.).  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, suivez l'une des solutions suivantes :  
  
-   Renommez les fichiers. Vérifiez que les noms de fichiers de tous les artefacts du projet BizTalk sont uniques.  
  
-   Vérifiez que le nom de type de chaque artefact du projet BizTalk est unique.  
  
## <a name="building-any-c-workflow-project-with-biztalk-mapper-shows-a-warning-regarding-version-conflict-for-envdtedll"></a>La création d'un projet de workflow C# à l'aide du Mappeur BizTalk affiche un avertissement relatif à un conflit de version pour EnvDTE.dll  
  
### <a name="problem"></a>Problème  
 La création d'un projet de workflow C# avec l'activité du Mappeur BizTalk affiche toujours l'avertissement suivant relatif à un conflit de version pour EnvDTE.dll.  
  
 Impossible de résoudre le conflit entre « EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a » et « EnvDTE, Version=7.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a ». Choix arbitraire de « EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a ».  Envisagez le remappage via app.config de l'assembly « EnvDTE, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a » de la version « 7.0.3300.0 » [] vers la version « 8.0.0.0 » [C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\PublicAssemblies\EnvDTE.dll] pour résoudre le conflit et supprimer l'avertissement. C:\Windows\Microsoft.NET\Framework\v4.0.30319\Microsoft.Common.targets(1360,9) : avertissement MSB3247 : des conflits entre différentes versions du même assembly dépendant ont été.  
  
 WorkflowConsoleApplication3 -> C:\Users\btslabs\Desktop\WorkflowConsoleApplication3\bin\Debug\WorkflowConsoleApplication3.exe  
  
### <a name="cause"></a>Cause  
 Ceci se produit en raison du fichier Microsoft.BizTalk.Mapper.OM.dll auquel l'activité du Mappeur fait référence.  
  
### <a name="resolution"></a>Résolution  
 Ignorez l'avertissement.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de mappages](../core/troubleshooting-maps.md)