---
title: "Débogage des Orchestrations à l’aide de Code personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, debugging
- building, debugging
ms.assetid: 94e569fa-8dea-4027-abb5-37b4a8015621
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47f69fa635a90db90c461f75c300334ccc499b94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-orchestrations-by-using-custom-code"></a>Débogage des orchestrations à l'aide d'un code personnalisé
Si votre orchestration va être testés dans un environnement de test ou si vous créez un prototype et que vous souhaitez modifier les valeurs des champs de message et des variables d’orchestration, vous pouvez écrire la sortie vers le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] console en utilisant le code suivant dans un  **Expression** forme :  
  
```  
System.Diagnostics.Debug.WriteLine(iResult);  
```  
  
 Vous devez placer ce **Expression** forme immédiatement après la forme qui effectue l’opération, afin que vous puissiez sortir le résultat pour le débogage.  
  
 Il est également possible d'écrire un simple débogueur personnalisé. Pour ce faire, créez une DLL de débogage avec une classe contenant une méthode qui accepte en entrée un message au format défini dans votre orchestration et référencé dans la DLL de débogage. Pour plus d’informations sur la transmission d’un message en tant que paramètre, consultez [comment utiliser des Expressions pour créer des objets et appeler des méthodes objet](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md).  
  
 Cette méthode peut afficher une boîte de dialogue de débogage qui contient une zone de liste ou une autre commande qui permet la modification des valeurs par l'utilisateur, regroupe le message modifié, puis le retransmet comme valeur de retour.  
  
 Définir une variable booléenne pour indiquer si l’orchestration est en mode débogage, puis, là où vous avez un point dans l’orchestration à laquelle vous souhaitez être en mesure de modifier les valeurs, vous pouvez ajouter un **décider** forme avec une dynamique branche qui s’exécute uniquement lorsque la variable de mode de débogage est définie sur True, ou lorsqu’une condition particulière survient que vous souhaitez examiner. Vous appelez la méthode à partir une **Expression** forme dans la branche active de la **décider**. Lorsque vous n’avez plus besoin de déboguer, vous définissez votre variable de mode de débogage sur False, ou supprimez la **décider** recompile puis recompilez l’orchestration.  
  
## <a name="to-debug-a-net-component-called-by-an-orchestration"></a>Pour déboguer un composant .NET appelé par une orchestration  
 Les étapes suivantes indiquent comment déboguer un composant .NET appelé par une orchestration.  
  
1.  Ouvrez le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de votre composant.  
  
2.  Définissez dans le composant un point d'arrêt sur la méthode qui est appelée par l'orchestration.  
  
3.  Cliquez sur le **déboguer** menu et sélectionnez **attacher au processus...** Pour afficher le **attacher au processus** boîte de dialogue.  
  
4.  Cliquez sur le **sélectionnez...** situé en regard du **attacher à :** zone de texte pour afficher le **sélectionner le Type de Code** boîte de dialogue.  
  
5.  Cliquez pour sélectionner l’option à **déboguer ces types de codes :** et sélectionnez **Managed** puis cliquez sur le **OK** bouton.  
  
6.  Cliquez pour sélectionner le **BTSNTSvc.exe** des **processus disponibles** puis cliquez sur le **attacher** bouton.  
  
7.  Envoyez un message à votre orchestration via un port de réception.  
  
8.  Le composant .NET doit être arrêté sur le point d'arrêt.  
  
9. Vous pouvez effectuer un débogage classique à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    > [!NOTE]
    >  Pour de meilleurs résultats, le composant .NET doit être enregistré dans le GAC (Global Assembly Cache).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface utilisateur du débogueur d’orchestration](../core/orchestration-debugger-user-interface.md)   
 [Débogage des Orchestrations](../core/debugging-orchestrations.md)