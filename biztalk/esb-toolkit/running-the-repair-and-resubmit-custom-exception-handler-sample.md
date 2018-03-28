---
title: Exécution de l’exemple de gestionnaire d’Exception personnalisé réparation et soumettez à nouveau | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7363c440-44aa-4d08-8290-72787d17ac60
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8b33765cbe3ca1c8c0c7c3e7679e543678325af
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="running-the-repair-and-resubmit-custom-exception-handler-sample"></a>L’exemple de gestionnaire d’exceptions personnalisée réparation et soumettez à nouveau en cours d’exécution
L’exemple de réparation et soumettez à nouveau gestionnaire d’exceptions personnalisé montre une technique extrêmement efficace permettant d’intégrer une intervention humaine dans ESB et Microsoft application basée sur BizTalk traite et implémente un modèle de conception utiles. L’exemple de code s’intègre en toute transparence dans le système de gestion d’exception ESB.  
  
 L’exemple montre comment vous pouvez utiliser un gestionnaire d’exceptions personnalisé dans une orchestration. Lorsqu’un processus dans l’orchestration (EAIProcess.odx) rencontre une erreur, le Gestionnaire d’exceptions génère et publie un message d’erreur ESB. Ce message d’erreur inclut dans sa charge utile les messages (y compris leurs propriétés de contexte de BizTalk liées) qui ont été « en vol » lorsque l’exception s’est produite et l’instance actuelle de System.Exception interceptée par le moteur d’Orchestration BizTalk. Lorsque cela se produit, un message « Refusé » et un message « Approved » sont conservées avec le message d’erreur.  
  
 Une deuxième orchestration nommée EAIProcessHandler.odx, qui est déployé dans une méthode découplée et agit comme un gestionnaire d’exceptions personnalisées, s’abonne au code d’erreur spécifique généré dans l’orchestration EAIProcess.odx et consomme le message d’erreur. Ce gestionnaire d’exceptions extrait les messages d’origine (comme des documents typés) et les instances de System.Exception persistantes à l’origine dans le message d’erreur.  
  
 Désormais, les messages d’origine deviennent disponibles pour le traitement avec toutes leurs propriétés de contexte d’origine. Le Gestionnaire d’exceptions personnalisé (EAIProcessHandler.odx) écrit ensuite le « Denied » et les messages « Approved » au système de fichiers dans les emplacements suivants :  
  
-   Message approuvé :  
  
    -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcess.PostApproval  
  
-   Message de refus de la réparation et soumettez à nouveau :  
  
    -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcessHandler.RepairSubmit  
  
-   Message de refus :  
  
    -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcessHandler.PostDecline  
  
 Le Gestionnaire d’exceptions sérialise le message « Denied » pour la réparation et soumettez à nouveau au système de fichiers à l’aide d’une instruction de traitement Microsoft InfoPath. Un modèle InfoPath permet à l’utilisateur à modifier le formulaire et soumettez à nouveau le résultat (voir Figure 1), qui démarre l’orchestration EAIProcess.odx qui valide le message.  
  
 ![Soumettez à nouveau de réparer](../esb-toolkit/media/ch6-repairresubmit.gif "§ 6-RepairResubmit")  
  
 **Figure 1**  
  
 **Un message de test généré par la réparation d’InfoPath et soumettez à nouveau modèle**  
  
 En outre, il est un port d’envoi générique appelé tous. Exceptions_FILE qui est configuré pour utiliser le pipeline GlobalFaultProcessor. Ce port s’abonne à toutes les exceptions dans le système, les deux BizTalk Échec de routage des messages de message et les messages d’erreur ESB. L’infrastructure de gestion d’Exception les normalise toutes dans un format unique et sérialise à l’aide d’une instruction de traitement InfoPath pour le dossier \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions.  
  
## <a name="installation"></a>Installation  
 Tous les exemples de gestion d’exception utilisent le même jeu de services principaux et les artefacts de l’application BizTalk. Par conséquent, vous devez installer les artefacts d’exemple de gestion d’exception qu’une seule fois pour être en mesure d’exécuter tous les l’exception des exemples de gestion. Pour plus d’informations sur la façon d’installer les exemples de gestion des exceptions, consultez [installant les exemples de gestion des exceptions](../esb-toolkit/installing-the-exception-management-samples.md).  
  
## <a name="running-the-sample-application"></a>Exécution de l'exemple d'application  
 **Pour exécuter l’exemple de réparation et soumettez à nouveau gestionnaire d’exceptions personnalisées**  
  
1.  Avant d’exécuter cet exemple pour la première fois, assurez-vous que l’emplacement de réception et l’URL de port d’envoi pointent vers les répertoires appropriés dans le dossier \Source\Samples\Exception Handling\Test\Filedrop. L’emplacement de réception doit spécifier le dossier EAIProcess.RequestPort, et les URL de port d’envoi doivent spécifier les dossiers EAIProcess.PostApproval et EAIProcessHandler.PostDecline.  
  
2.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
3.  Démarrer l’exemple en copiant le fichier d’exemple nommé Request_EAIProcessHandler.xml, situé dans le dossier \Source\Samples\Exception Handling\Test\Data, dans le dossier spécifié pour l’emplacement de réception de la EAIProcess.RequestPort_FILE : \Source\Samples\ Exception Handling\Test\Filedrop\EAIProcess.RequestPort.  
  
4.  Ouvrez le dossier nommé EAIProcessHandler.PostDecline (dans le dossier \Source\Samples\Exception Handling\Test\Filedrop). Vous verrez le message « Refusé * » généré par l’orchestration d’exceptions.  
  
5.  Ouvrez le dossier nommé EAIProcessHandler.RepairSubmit (dans le dossier \Source\Samples\Exception Handling\Test\Filedrop). Vous verrez un message « RepairSubmit » généré par l’orchestration de gestion des exceptions.  
  
6.  Double-cliquez sur le fichier RepairSubmit pour l’ouvrir dans le modèle InfoPath approprié. Vous verrez le message prêt pour la modifier et nouvelle soumission.  
  
7.  Modifiez la valeur de la **prix unitaire** champ **0** à **2**, puis cliquez sur le **envoyer** situé dans la barre d’outils d’InfoPath formulaire à envoyer le document modifié dans BizTalk pour le traitement. Emplacement de réception de la soumission process utilise un HTTP configuré BizTalk.  
  
8.  Accédez au dossier EAIProcess.PostApproval (dans le dossier \Source\Samples\Exception Handling\Test\Filedrop). Vous voyez maintenant le document « Approbation * » qui contient la valeur mise à jour pour le prix unitaire.  
  
## <a name="how-the-sample-works"></a>Fonctionne de l’exemple  
 Le message que vous envoyez Active l’orchestration EAIProcess. Lorsque l’orchestration EAIProcess traite le message, il tente de diviser 1 par le prix unitaire. Étant donné que le prix unitaire est égal à zéro, une exception de division par zéro se produit. Code du Gestionnaire d’événements de l’orchestration intercepte cette exception et crée un message d’erreur. La quantité commandée dans le message est supérieure à 10, donc la logique métier en décide que cette exception a un **FaultCode** champ à la valeur de **1000**.  
  
 L’orchestration EAIProcess publie le message d’erreur dans la boîte de Message BizTalk via un port à liaison directe, et l’orchestration se termine.  
  
 Une orchestration de gestionnaire d’erreur personnalisée nommée EAIProcessHandler, qui s’abonne aux messages avec un **FaultCode** champ à la valeur de **1000**, récupère le message d’erreur. Le code de l’orchestration crée le message « Denied » et le fichier InfoPath, puis il place dans les dossiers EAIProcessHandler.PostDecline et EAIProcessHandler.RepairSubmit prêt pour une intervention humaine.