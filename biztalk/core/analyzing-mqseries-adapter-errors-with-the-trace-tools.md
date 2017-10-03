---
title: "Analyse des erreurs de l’adaptateur MQSeries avec les outils de Trace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, about Adapter Trace Utility
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- errors, MQSeries adapters
- MQSeries adapters, Adapter Trace Utility
- Adapter Trace Utility, running
- MQSeries adapters, errors
- Adapter Trace Utility
ms.assetid: fdc73d99-3b73-491d-9b2f-7064364fefa7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8880197e58f6a499cc63e8b6ec89f67af9f0086
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="analyzing-mqseries-adapter-errors-with-the-trace-tools"></a>Analyse des erreurs de l’adaptateur MQSeries avec les outils de Trace
Les outils de suivi permettent d'analyser les échecs relatifs à la messagerie lors de l'exécution d'une application. Avec l'adaptateur MQSeries, vous devez utiliser deux outils : trace.cmd pour l'adaptateur et l'application BizTalk application, et MQSTrace.cmd pour MQSAgent. Les deux outils utilisent tracelog.exe. Vous devez installer tracelog.exe si vous ne l’avez pas déjà.  
  
 Trace.cmd et MQSTrace.cmd, vous devez définir une option (**-outils**) afin que ces outils peuvent trouver le fichier tracelog.exe.  
  
## <a name="install-the-trace-utility"></a>Installation de l'utilitaire de suivi  
 Pour installer l'utilitaire de suivi de l'adaptateur BizTalk, procédez comme suit :  
  
1.  Pour télécharger le fichier Tracelog.exe, visitez le site Web de téléchargement Microsoft Platform SDK à [http://go.microsoft.com/fwlink/?LinkId=21975](http://go.microsoft.com/fwlink/?LinkId=21975).  
  
2.  Démarrer le programme d’installation Web du Kit de développement logiciel Platform en cliquant sur le lien pour le **PSDK-x86.exe** fichier au bas de la page Web.  
  
3.  Lorsque vous y êtes invité, choisissez de procéder à une installation personnalisée.  
  
4.  Dans la boîte de dialogue **Installation personnalisée** , désactivez toutes les cases à cocher relatives aux composants disponibles.  
  
5.  Développez le composant de **kit de développement SDK principal Microsoft Windows** , puis le composant **Outils** .  
  
6.  Choisissez le composant **Outils (Intel 64 bits)** et cliquez sur **Installation sur le disque dur local**.  
  
7.  Cliquez sur **Suivant**, puis de nouveau sur **Suivant** pour démarrer l'installation.  
  
8.  Recherchez le *lecteur*:\\*MicrosoftPlatformSDKInstallationFolder\bin* dossier, puis copiez le fichier Tracelog.exe dans le dossier d’installation de Microsoft BizTalk Server. qui inclut également le fichier Trace.cmd.  
  
## <a name="enable-the-trace-utility"></a>Activation de l'utilitaire de suivi  
 Pour activer l'utilitaire de suivi de l'adaptateur BizTalk dans BizTalk Server, procédez comme suit :  
  
1.  Déplacer vers le répertoire contenant trace.cmd. L’emplacement par défaut est Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] active.  
  
2.  Tapez la commande suivante, en remplaçant le répertoire contenant le fichier tracelog.exe sur votre ordinateur par le répertoire entre guillemets, puis appuyez sur ENTRÉE :  
  
     **trace - tools « c:\Program Files\Microsoft SDK\Bin »**  
  
3.  Accédez au répertoire contenant MQSTrace.cmd.  
  
4.  Tapez la commande suivante, en remplaçant le répertoire contenant le fichier tracelog.exe sur votre ordinateur par le répertoire entre guillemets, puis appuyez sur ENTRÉE :  
  
     **MQSTrace-« c:\Program Files\Microsoft SDK\Bin » des outils**  
  
## <a name="run-the-trace-utility"></a>Exécution de l'utilitaire de suivi  
 Pour exécuter l'utilitaire de suivi de l'adaptateur BizTalk, procédez comme suit :  
  
1.  À l’invite de commandes, tapez **trace.cmd-start - high**, puis appuyez sur ENTRÉE.  
  
2.  Exécutez le scénario d'échec.  
  
3.  À l’invite de commandes, tapez **trace.cmd-stop**, puis appuyez sur ENTRÉE.  
  
4.  Le fichier bts2006.bin contient la sortie de l'outil de suivi. Contactez les Services de support technique Microsoft à des fins d'analyse. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).  
  
 Pour exécuter l'utilitaire de suivi MQSAgent, procédez comme suit :  
  
1.  À l’invite de commandes, tapez **MQSTrace.cmd-start - high**, puis appuyez sur ENTRÉE.  
  
2.  Exécutez le scénario d'échec.  
  
3.  À l’invite de commandes, tapez **MQSTrace.cmd-stop**.  
  
4.  Le fichier MQSAdapterTrace.bin contient la sortie de l'outil de suivi. Contactez les Services de support technique Microsoft à des fins d'analyse. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).