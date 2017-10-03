---
title: "Appel des membres statiques d’une classe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a51171c-8de0-45dd-8659-f674cf27acbe
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2128bf6cb71c773cd31be497765e39b0d7815b4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-static-members-of-a-class"></a>Appel de membres statiques d'une classe
Par défaut, le moteur de règles exige que vous déclariez une instance d'une classe .NET pour exécuter une stratégie appelant un membre statique de cette classe. Vous pouvez modifier ce comportement en modifiant la valeur de la **StaticSupport** clé de Registre sous **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0** à une des valeurs dans le tableau suivant.  
  
|Valeur de registre StaticSupport|Comportement du moteur de règles|  
|----------------------------------|--------------------------|  
|0|Valeur par défaut. Le moteur de règles suit le modèle de BizTalk Server 2004, selon lequel la méthode statique est appelée uniquement lorsqu'une instance de la classe .NET est déclarée.|  
|1|Aucune instance d'objet n'est requise. La méthode statique est appelée lors de l'évaluation ou de l'exécution de la règle.|  
|2|Aucune instance d'objet n'est requise. La méthode statique est appelée au moment de la conversion de la stratégie si tous les paramètres sont constants. Les performances s'en trouvent optimisées car la méthode statique n'est appelée qu'une seule fois, et ce même si elle intervient dans plusieurs règles. Notez que les méthodes statiques utilisées en tant qu'actions ne sont pas exécutées au moment de la conversion, à la différence des méthodes utilisées en tant que paramètres.|  
  
## <a name="adding-and-changing-the-staticsupport-registry-key"></a>Ajout et modification de la clé de registre StaticSupport  
 Si vous ne voyez pas le **StaticSupport** clé de Registre sous **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, vous devez l’ajouter en effectuant les étapes suivantes.  
  
 **Pour ajouter la clé de Registre StaticSupport**  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **RegEdit**, puis cliquez sur **OK**.  
  
2.  Développez **HKEY_LOCAL_MACHINE**, développez **logiciel**, développez **Microsoft**, développez **BusinessRules**, puis sélectionnez **3.0**.  
  
3.  Dans le volet droit, cliquez sur, pointez sur **nouveau**, puis cliquez sur **valeur DWORD**.  
  
4.  Pour **nom**, type **StaticSupport**.  
  
 Si le **StaticSupport** clé de Registre existe déjà, et vous devez modifier sa valeur, procédez comme suit.  
  
> [!IMPORTANT]
>  Si BizTalk est installé sur un ordinateur 64 bits, vous pouvez alors ajouter **StaticSupport** clé de Registre à l’aide d’une des options suivantes :  
>   
>  -   Regardez sous HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0. Si cette clé existe, vous pouvez alors ajouter **StaticSupport** ici.  
> -   Une autre option consiste à placer **StaticSupport** dans les **.exe.config de BTNTsvc [64]** de fichiers, comme ici tous les paramètres de remplacement Nouveautés dans le Registre.  Par ailleurs, certains peuvent avancer l’argument que l’utilisation de cette option est préférable étant donné qu’elle permet d’isoler la modification du comportement par défaut à BizTalk uniquement, tandis que les paramètres du Registre sont communs au système d’exploitation.  
  
 **Pour modifier la valeur de la clé de Registre StaticSupport**  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **RegEdit**, puis cliquez sur **OK**.  
  
2.  Développez **HKEY_LOCAL_MACHINE**, développez **logiciel**, développez **Microsoft**, développez **BusinessRules**, puis développez **3.0**.  
  
3.  Double-cliquez sur le **StaticSupport** Registre de clé, ou faites un clic droit, puis cliquez **modifier**.