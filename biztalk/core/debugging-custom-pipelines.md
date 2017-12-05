---
title: "Débogage des Pipelines personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27e5445a-6415-4c52-a450-b74a71fc4aa2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be0c8714f0349ad415beca010795d2cb0b57aabb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="debugging-custom-pipelines"></a>Débogage des pipelines personnalisés
Lorsque le traitement d'un message dans votre pipeline personnalisé échoue, utilisez les outils de débogage au niveau du code source pour identifier et corriger les problèmes. Le débogage au niveau du code source s'effectue par l'intermédiaire du débogueur  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] en joignant BTSNTSVC.exe (si le pipeline personnalisé est déployé) ou Pipeline.exe (en cas d'utilisation de l'outil pipeline autonome).  
  
## <a name="procedures"></a>Procédures  
 Les procédures suivantes permettent de déboguer les pipelines personnalisés.  
  
### <a name="how-to-debug-a-deployed-pipeline"></a>Débogage d'un pipeline déployé  
 Les requêtes de suivi via la page Hub du groupe et les observateurs d'événements fournissent des informations utiles au sujet des échecs de traitement des messages dans les composants déployés. Ces informations permettent souvent de déterminer l'origine d'un problème. Dans le cas d'un pipeline personnalisé, le débogage au niveau du code source permet d'identifier les sections de code problématiques.  
  
##### <a name="to-debug-a-deployed-custom-pipeline-using-visual-studio"></a>Pour déboguer un pipeline personnalisé déployé à l'aide de Visual Studio  
  
1.  Chargez la solution de projet du pipeline personnalisé dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Modifiez le chemin de sortie pour votre solution à  *\<dossier d’Installation\>*\Pipeline Components. Dans l’Explorateur de solutions, cliquez sur votre projet et cliquez sur l’onglet Générer, puis modifiez le chemin de sortie en cliquant sur le **Parcourir** bouton et en sélectionnant le  *\<dossier d’Installation\>* Répertoire \Pipeline components.  
  
3.  Depuis [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], déployez la solution en cliquant sur **générer** &#124; **Déployer**.  
  
4.  Redémarrez l'instance de l'hôte qui exécute le pipeline. À l’aide de la console Administration de BizTalk Server, accédez à l’instance d’hôte qui exécute le pipeline, cliquez sur l’instance d’hôte, puis cliquez sur **redémarrer**.  
  
5.  Attacher le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] débogueur BTSNtSvc.exe. Cela est possible en cliquant sur **déboguer** &#124; **Attacher au processus**et cliquez sur Afficher les processus de toutes les sessions, puis double-cliquez sur BTSNTSVC.exe.  
  
6.  Définir les points d'arrêt.  
  
7.  Laissez un message à l'emplacement approprié pour initier le composant de pipeline personnalisé. Le traitement doit s'arrêter aux points d'arrêt définis.  
  
> [!NOTE]
>  Si votre code génère une exception, BizTalk Server l'intercepte et suspend le message. Pour éviter cela, interrompez le traitement aux exceptions de première chance.  
  
### <a name="how-to-debug-using-pipelineexe"></a>Débogage à l'aide de Pipeline.exe  
 Vous pouvez également tester des pipelines personnalisés à l’aide de Pipeline.exe. Cela a l’avantage de ne pas vous obliger à déployer le pipeline au ne pas en cours d’exécution dans des conditions similaires en production.  
  
> [!NOTE]
>  Si votre pipeline personnalisé utilise l'assembleur ou le désassembleur de fichier plat, Pipeline.exe ne s'exécutera pas correctement. Cela est dû au fait que Pipeline.exe n'a pas accès à la base de données BizTalk. Une solution consiste à supprimer de l’assembleur / composants désassembleur et de les tester séparément avec FFDasm.exe et FFAsm.exe. Consultez [outils de Pipeline](../core/pipeline-tools.md) pour plus d’informations.  
  
##### <a name="to-debug-a-custom-pipeline-using-pipelineexe-and-visual-studio"></a>Pour déboguer un pipeline personnalisé à l'aide de Pipeline.exe et de Visual Studio  
  
1.  Chargez la solution de projet du pipeline personnalisé dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Modifiez le chemin de sortie pour votre solution à  *\<dossier d’Installation\>*\Pipeline Components. Dans l’Explorateur de solutions, cliquez sur votre projet et cliquez sur l’onglet Générer, puis modifiez le chemin de sortie en cliquant sur le **Parcourir** bouton et en sélectionnant le  *\<dossier d’Installation\>* Répertoire \Pipeline components.  
  
3.  Modifiez l'action de démarrage pour votre solution. Dans l’Explorateur de solutions, cliquez sur votre projet, cliquez sur l’onglet Déboguer, cliquez sur Démarrer le programme externe, puis cliquez sur **...** Accédez à  *\<dossier d’Installation\>*\SDK\Utilities\PipelineTools et choisissez Pipeline.exe. Sous les Options de démarrage, entrez les arguments de ligne de commande appropriées pour votre composant. Pour plus d’informations sur Pipeline.exe, voir [outils de Pipeline](../core/pipeline-tools.md). La configuration typique spécifie le pipeline et un exemple de fichier :  
  
    ```  
    <Path>\YourPipeline.btp -d <Path>\YourTestFile.txt -c  
    ```  
  
4.  Définissez vos points d'arrêt.  
  
5.  Appuyez sur F5 pour commencer le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de pipeline](../core/pipeline-tools.md)