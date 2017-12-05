---
title: "Étape 1 : Créer et déployer le projet BizTalk vPrev pour la réception d’un IDOC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, building and deploying previous version of BizTalk project for receiving an IDOC
- migrating, building and deploying previous version of BizTalk project for receiving an IDOC
- migration
ms.assetid: ab6bdf9a-dca5-4acd-97b2-a9afe9792978
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f99971a421530e4901c8bbac6533809a0f2f273c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc"></a>Étape 1 : Créer et déployer le projet BizTalk vPrev pour la réception d’un IDOC
![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous générez et déployez votre projet BizTalk de vPrev existant pour recevoir un IDOC à partir d’un système SAP.  
  
> [!NOTE]
>  Vous n’avez pas besoin d’apporter de modification au projet BizTalk vPrev.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer d’un projet BizTalk de vPrev pour recevoir un IDOC ORDERS03 à partir d’un système SAP.  
  
### <a name="to-build-and-deploy-the-vprev-biztalk-project"></a>Pour générer et déployer le projet BizTalk vPrev  
  
1.  Créer un fichier de clé de nom fort requis pour générer et déployer la solution. Pour créer un fichier de clé de nom fort, procédez comme suit :  
  
    1.  Démarrez l’invite de commandes Visual Studio.  
  
    2.  À l’invite de commandes, accédez au dossier où vous souhaitez créer le fichier de clé. Par exemple, tapez **cd C:\Sample**, puis appuyez sur ENTRÉE.  
  
    3.  À l’invite de commandes, tapez **sn -k \<nom de fichier de clé\>.snk**, puis appuyez sur ENTRÉE.  
  
2.  Cliquez sur le nom de la solution BizTalk dans l’Explorateur de solutions, puis cliquez sur **propriétés**. Dans le **Pages de propriétés** boîte de dialogue zone, procédez comme suit :  
  
    1.  Cliquez sur **propriétés de Configuration** dans le volet gauche et assurez-vous que les cases à cocher la **générer** et **déployer** les colonnes sont sélectionnées.  
  
    2.  Cliquez sur **OK**.  
  
3.  Cliquez sur le projet BizTalk dans l’Explorateur de solutions, puis cliquez sur **propriétés**. Dans le **Pages de propriétés** boîte de dialogue zone, procédez comme suit :  
  
    1.  Dans le volet gauche, développez **propriétés communes**, puis cliquez sur Assembly.  
  
    2.  Dans le volet droit, sous la **nom fort** catégorie, pour le **fichier de clé d’Assembly** propriété, fournissez le chemin d’accès au fichier de clé d’assembly vous avez créé précédemment.  
  
    3.  Cliquez sur **OK**.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **générer la Solution**.  
  
5.  Une fois la solution générée avec succès, cliquez sur le nom de la solution, puis cliquez sur **déployer la Solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Créer et configurer un WCF-Custom port de réception et le configurer pour recevoir des IDOC à partir d’un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], comme décrit dans [étape 2 : configurer un Port de réception WCF-Custom unidirectionnel](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Migration d’un projet BizTalk SAP de réception d’un IDOC](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)