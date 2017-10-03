---
title: Le Pipeline ESB erreur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a57752b1-8bca-4534-9e5b-7ce721a9490a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebd9a6cecf5353ab72cea0d67b06f3402fc1716a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-fault-processor-pipeline"></a>Le Pipeline ESB erreur
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installe un port d’envoi nommé tous. Les exceptions qui utilise le ESBFaultProcessor pipeline d’envoi. Figure 1 présente les propriétés de l’ensemble. Exceptions de port d’envoi.  
  
 ![Port d’envoi de toutes les Exceptions](../esb-toolkit/media/ch4-allexceptionssendport.gif "AllExceptionsSendPort de chapitre 4")  
  
 **Figure 1**  
  
 **La configuration de l’ensemble. Exceptions de port d’envoi, y compris son utilisation du pipeline ESBFaultProcessor**  
  
 Le pipeline ESBFaultProcessor contient les composants suivants : ESB Exception encodeur, ESB analyse BAM (Business Activity) de mise hors tension et ESB transformer.  
  
 Tous les. Exceptions de port s’abonne à tous les messages d’erreur ESB et à tous les messages générés par le mécanisme de routage des messages a échoué BizTalk d’envoi. Figure 2 illustre le filtre de l’ensemble des paramètres de propriété. Exceptions de port d’envoi.  
  
 ![Filtre de Port d’envoi](../esb-toolkit/media/ch4-filtersendport.gif "FilterSendPort de chapitre 4")  
  
 **Figure 2**  
  
 **La propriété filter de l’ensemble. Exceptions de port définit l’abonnement de port d’envoi**  
  
## <a name="the-fault-processor-pipeline-exception-encoder-component"></a>Le composant encodeur erreur processeur Pipeline (Exception)  
 Le composant de pipeline encodeur d’Exception ESB normalise les messages d’erreur dans le mécanisme d’ESB Échec de l’Orchestration Exception routage et le mécanisme de routage des messages a échoué BizTalk en canoniques messages conformes à la déclaration d’Exception ESB schéma.  
  
 Pour une exception d’échec du routage des exceptions d’Orchestration, le composant enrichit et sérialise toutes les propriétés de message d’erreur, les messages XLANG, les propriétés de contexte, et **System.Exception** informations dans un message XML.  
  
 Pour une exception d’échec de routage des messages, le composant enrichit les données en ajoutant le nom de l’application et les autres propriétés ambiantes, et elle s’applique à l’espace de noms du schéma pour le contenu du message XML sortant.  
  
 Si vous le souhaitez, le composant de pipeline encodeur d’Exception ESB peut s’appliquent également Microsoft InfoPath dans le message sortant, les instructions de traitement. Vous pouvez modifier les instructions InfoPath en définissant les propriétés du composant de pipeline en mode Création. Les propriétés de temps de trois conception suivants affectent le comportement d’exécution du composant de pipeline encodeur d’Exception ESB :  
  
-   **EscapeCDATA.** Cette propriété détermine si le composant échappe les **CDATA** sections trouvées dans persistant messages afin que InfoPath permettre les afficher correctement.  
  
-   **FaultDocumentNamespace.** Cette propriété a la valeur par défaut **http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**. Ce paramètre peut être modifié pour utiliser un espace de noms sortant personnalisé pour les messages persistants.  
  
-   **ProcessingInstruction.** Cette propriété peut contenir toute instruction de traitement InfoPath qui est conforme au schéma d’erreur ESB rapports d’exceptions. La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut un modèle InfoPath qui est conforme à l’instruction de traitement suivante.  
  
    ```  
    <?mso-infoPathSolution solutionVersion="1.0.0.346" productVersion="11.0.6565"  
    PIVersion="1.0.0.0"   
    href=file:///\\localhost\publish\Microsoft.Practices.ESB.ExceptionHandling.InfoPath.Reporting.xsn  
    name="urn:schemas-microsoft-com:office:infopath:  
    Microsoft-Practices-ESB-ExceptionHandling-InfoPath-Reporting:  
    http---schemas-microsoft-biztalk-practices-esb-com-exceptionhandling"  
    language="en-us" ?><?mso-application progid="InfoPath.Document"?>  
    ```  
  
## <a name="the-fault-processor-pipeline-bam-tracker-component"></a>Le composant de mise hors tension de pannes processeur Pipeline BAM  
 Le composant de pipeline du dispositif de suivi BAM ESB reçoit le message à partir du composant ESB Exception encodeur et écrit des données de l’erreur sélectionnée dans les tables d’importation principale BAM créés pendant l’installation de l’infrastructure de gestion d’Exception ESB.  
  
 Le composant BAM de la mise hors tension ESB utilise le **GetEventStream** méthode du contexte de pipeline pour ajouter les champs suivants en tant qu’un enregistrement d’activité à la base de données d’importation principale BAM :  
  
-   **Application**  
  
-   **Description**  
  
-   **FaultSeverity**  
  
-   **ServiceName**  
  
-   **ErrorType**  
  
-   **FaultCode**  
  
-   **MachineName**  
  
-   **MessageID**  
  
-   **DateTime**  
  
-   **FaultDescription**  
  
-   **Portée**  
  
-   **FailureCategory**  
  
-   **FaultGenerator**  
  
-   **ServiceInstanceID**  
  
 Le composant de dispositif de suivi BAM ESB utilise l’identificateur de message (le **MessageID** propriété) la valeur du message d’erreur ESB en tant qu’ID d’activité BAM. Le composant BAM de la mise hors tension ESB expose deux propriétés de temps de conception que vous pouvez définir pour modifier son comportement au moment de l’exécution :  
  
-   **Activé.** Cette propriété détermine si le composant traitera le message et écrire dans la base de données BAM. Lorsque la valeur **False**, le composant transmet le message au composant suivant dans le pipeline.  
  
-   **FaultDocumentNamespace.** Cette propriété a la valeur par défaut **http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**.  
  
## <a name="the-fault-processor-pipeline-transform-component"></a>Transformer le composant Pipeline du processeur de pannes  
 Le pipeline ESB erreur utilise le composant de pipeline ESB transformer pour exécuter un mappage BizTalk qui convertit le message d’erreur ESB codé dans un format qui correspond au schéma de l’adaptateur SQL de BizTalk (ExceptionSql.xsd). Le composant transmet alors le message transformé à l’adaptateur SQL, qui insère le message d’erreur ESB dans la base de données du portail de gestion ESB.  
  
 Le composant de pipeline ESB transformer expose trois propriétés au moment du design qui peuvent être modifiées pour modifier son comportement au moment de l’exécution :  
  
-   **Activé.** Cette propriété Active ou désactive le composant.  
  
-   **Valider.** Cette propriété spécifie si un message doit être validée.  
  
-   **MapName.** Cette propriété contient le nom de la carte doit être exécutée pour traduire le message pour le stockage dans la base de données du portail de gestion ESB. Voici la valeur par défaut.  
  
    ```  
    Microsoft.Practices.ESB.ExceptionHandling.Maps.FaultMessage_to_ExceptionSql,  
    Microsoft.Practices.ESB.ExceptionHandling.Maps,  
    Version=2.0.0.0,  
    Culture=neutral,  
    PublicKeyToken=c2c8b2b87f54180a  
    ```  
  
 Tous les composants de pipeline après exécution, l’adaptateur de base de données SQL de BizTalk Server insère le message d’erreur dans la base de données du portail de gestion ESB.