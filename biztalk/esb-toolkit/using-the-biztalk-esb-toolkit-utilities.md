---
title: "À l’aide d’utilitaires BizTalk ESB Toolkit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2dc05ac-831a-44e1-bd44-e41398552ab1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36902e2c5e90ce1b02f40f6994f150fa4c421c7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-biztalk-esb-toolkit-utilities"></a>À l’aide d’utilitaires BizTalk ESB Toolkit
Cette section décrit les différents utilitaires inclus dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 **Utilitaire d’importation d’itinéraire ESB**  
  
 Cet utilitaire se trouve dans le répertoire \bin de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et est nommé EsbImportUtil.exe. Cet utilitaire peut être utilisé pour publier ou déployer l’itinéraire XML dans la base de données ESBItineraryDB.  
  
 La syntaxe de l’utilitaire est comme suit :  
  
```  
>EsbImportUtil <Parameter1> <Value> <parameter2> <Value>...  
```  
  
 Il peut accepter divers paramètres sont les suivants :  
  
 / ? : \<Présentent les paramètres qui aident à >  
  
 / f: \<chemin d’accès au fichier de feuille de route xml >  
  
 / c: \<publié &#124; déployé >  
  
 / n: \<nom de la feuille de route par défaut >  
  
 / v: \<version de feuille de route par défaut (format « major.minor ») >  
  
 /o : \<remplacer en mode silencieux >  
  
 Voici quelques exemples d’utilisation de cet utilitaire.  
  
 Pour publier la base de données de l’itinéraire :  
  
```  
>EsbImportUtil /f:myitinerary.xml /c:published  
```  
  
 Pour déployer la base de données de l’itinéraire :  
  
```  
>EsbImportUtil  /f:myitinerary.xml /c:deployed  
```  
  
 **Configuration de l’authentification unique conserver l’utilitaire**  
  
 Cet utilitaire se trouve dans le répertoire \bin de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et est nommé Microsoft.Practices.ESB.PersistConfigurationTool.exe. Cet utilitaire peut être utilisé pour rendre persistantes les informations de configuration ESB dans la base de données BizTalk SSO. Cela peut également servir à afficher des informations de configuration et de supprimer les informations de configuration à partir de la base de données SSO.  
  
 La syntaxe de l’utilitaire est comme suit :  
  
 **Pour ajouter une section de configuration :**  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /P /F:app.config /S:SectionName /A:ApplicationName  
```  
  
> [!NOTE]
>  Si /S n’est pas fourni, les sections suivantes seront ajoutées : connectionStrings, esb, esb.resolver et cachingConfiguration.  
  
 **Pour supprimer une section :**  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /R /S:SectionName  
```  
  
 Pour afficher une section existante, utilisez les commutateurs de l’application et de la section avec le commutateur /V.  
  
 Pour définir l’administrateur du nom de groupe, utilisez le commutateur AG:AdminGroupName.  
  
 Pour définir le nom de groupe d’utilisateurs, utilisez le commutateur UG:UserGroupName.