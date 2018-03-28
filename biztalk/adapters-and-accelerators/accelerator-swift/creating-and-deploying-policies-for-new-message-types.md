---
title: Création et déploiement de stratégies pour les nouveaux Types de messages | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43343238-ec45-44ed-a230-9e234bd22d05
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b826b3ee9408caf91fe5adcb2177d709f885a6e1
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="creating-and-deploying-policies-for-new-message-types"></a><span data-ttu-id="86390-102">Création et déploiement de stratégies pour les nouveaux Types de Message</span><span class="sxs-lookup"><span data-stu-id="86390-102">Creating and Deploying Policies for New Message Types</span></span>
<span data-ttu-id="86390-103">Pour créer et déployer des stratégies pour les nouveaux types de message :</span><span class="sxs-lookup"><span data-stu-id="86390-103">To create and deploy policies for new message types:</span></span>  
  
1.  <span data-ttu-id="86390-104">Créer un dossier portant le nom du type de message à l’intérieur du dossier MX Messages.</span><span class="sxs-lookup"><span data-stu-id="86390-104">Create a folder with the name of the message type inside MX Messages folder.</span></span> <span data-ttu-id="86390-105">Par exemple, dans ce cas le nom du dossier serait setr.004.001.02.</span><span class="sxs-lookup"><span data-stu-id="86390-105">For example, in this case the name of the folder would be setr.004.001.02.</span></span>  
  
    ```csharp  
    (<xs:complexType name="Document">  
        <xs:sequence>  
            <xs:element name="setr.004.001.02" type="setr.004.001.02"/>  
        </xs:sequence>  
    </xs:complexType>)  
    ```  
  
2.  <span data-ttu-id="86390-106">Placez le fichier de schéma (\*.xsd), ainsi que le maître résultant / stratégie de validation du fichier pour ce type de message dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="86390-106">Place the schema file (\*.xsd) along with the resulting master / validation policy file for this message type in this folder.</span></span>  
  
3.  <span data-ttu-id="86390-107">Mettre à jour le MXMessageTypeKeywordList.xml (C:\Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools) avec un nom de mot clé.</span><span class="sxs-lookup"><span data-stu-id="86390-107">Update the MXMessageTypeKeywordList.xml (C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools) with a keyword name.</span></span> <span data-ttu-id="86390-108">Ce nom doit être les quatre premières lettres du nom du dossier de message.</span><span class="sxs-lookup"><span data-stu-id="86390-108">This name must be the first four letters of the message folder name.</span></span> <span data-ttu-id="86390-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="86390-109">For example,</span></span>  
  
    ```csharp  
    (<Keyword name ="setr" />)  
    ```  
  
4.  <span data-ttu-id="86390-110">Pour créer le maître spécifique, les stratégies de validation, effectuer une copie de la base, les fichiers de stratégie de validation existants de message et de le placer dans le nouveau dossier de message.</span><span class="sxs-lookup"><span data-stu-id="86390-110">To create specific master / validation policies, take a copy of the master / validation policy files of the existing message and place it in the new message folder.</span></span>  
  
5.  <span data-ttu-id="86390-111">Modifiez toutes les références aux types de messages dans le master / stratégie de validation afin de refléter les nouveaux types de message.</span><span class="sxs-lookup"><span data-stu-id="86390-111">Change all of the references to message types in the master / validation policy to reflect the new message types.</span></span>  
  
## <a name="message-naming-conventions"></a><span data-ttu-id="86390-112">Conventions d’affectation de noms de message</span><span class="sxs-lookup"><span data-stu-id="86390-112">Message Naming Conventions</span></span>  
 <span data-ttu-id="86390-113">Suivre les conventions pour les noms de message :</span><span class="sxs-lookup"><span data-stu-id="86390-113">Follow these conventions for message names:</span></span>  
  
-   <span data-ttu-id="86390-114">**En remplaçant le nom du message**: si le nouveau nom de message est swift.if.ia.setr.004.001.02 et l’ancien message dont les fichiers stratégie ont été utilisées est pacs.002.001.02, puis remplacez toutes les occurrences de pacs.002.001.02 avec SWIFT.If.IA.setr.004.001.02 dans les fichiers de stratégie.</span><span class="sxs-lookup"><span data-stu-id="86390-114">**Replacing the message name**: If the new message name is swift.if.ia.setr.004.001.02 and the old message whose policy files have been used is pacs.002.001.02, then replace all of the occurrences of pacs.002.001.02 with swift.if.ia.setr.004.001.02 within the policy files.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86390-115">Nom du message est le nom du fichier de schéma qui a été téléchargé et type de message est le nom du type de document dans le message.</span><span class="sxs-lookup"><span data-stu-id="86390-115">Message name is the name of the schema file which has been downloaded and message type is the name of the document type in the message.</span></span>  
  
-   <span data-ttu-id="86390-116">Conservez le nom des fichiers de stratégie dans le même que le schéma du message lui-même.</span><span class="sxs-lookup"><span data-stu-id="86390-116">Keep the name of the policy files the same as the message schema itself.</span></span> <span data-ttu-id="86390-117">Par exemple, swift.if.ia.setr.004.001.02.xsd aura suivant _Validation_Policy.xml _Master_Policy.xml et swift.if.ia.setr.004.001.02 du swift.if.ia.setr.004.001.02 stratégies.</span><span class="sxs-lookup"><span data-stu-id="86390-117">For example, swift.if.ia.setr.004.001.02.xsd will have following policies swift.if.ia.setr.004.001.02 _Master_Policy.xml and swift.if.ia.setr.004.001.02 _Validation_Policy.xml.</span></span>  
  
-   <span data-ttu-id="86390-118">**Caractères spéciaux**: si le nom du message compte des caractères spéciaux, création d’un fichier de stratégie requiert une convention légèrement différente.</span><span class="sxs-lookup"><span data-stu-id="86390-118">**Special characters**: If the message name has any special characters in it, then creating a policy file requires a slightly different convention.</span></span> <span data-ttu-id="86390-119">Si le nom du message est, par exemple, swift.if.ia$setr.004.001.02, alors que vous devez modifier le nom du fichier de stratégie pour le nom du message avec les caractères spéciaux qui est remplacées par «. »</span><span class="sxs-lookup"><span data-stu-id="86390-119">If the message name is, for example, swift.if.ia$setr.004.001.02, then you must change the name of the policy file to the message name with the special characters being replaced by “.”</span></span> <span data-ttu-id="86390-120">Par exemple, si le nom du fichier de schéma de message est swift.if.ia$setr.004.001.02.xsd, la stratégie maître résultante serait swift.if.ia.setr.004.001.02_Master_Policy.xml.</span><span class="sxs-lookup"><span data-stu-id="86390-120">For example, if the name of the message schema file is swift.if.ia$setr.004.001.02.xsd, then the resulting master policy would be swift.if.ia.setr.004.001.02_Master_Policy.xml.</span></span>  
  
     <span data-ttu-id="86390-121">Le fichier de stratégie principal doit également être modifiées pour refléter le nouveau nom dans les balises suivantes :</span><span class="sxs-lookup"><span data-stu-id="86390-121">The master policy file also needs to be changed to reflect the new name in the following tags:</span></span>  
  
    -   <span data-ttu-id="86390-122">\<ruleset name="swift.if.ia.setr.004.001.02_Master_Policy"\></span><span class="sxs-lookup"><span data-stu-id="86390-122">\<ruleset name="swift.if.ia.setr.004.001.02_Master_Policy"\></span></span>  
  
    -   <span data-ttu-id="86390-123"><rule name="swift.if.ia.setr.004.001.02_Policy_List"</span><span class="sxs-lookup"><span data-stu-id="86390-123"><rule name="swift.if.ia.setr.004.001.02_Policy_List"</span></span>