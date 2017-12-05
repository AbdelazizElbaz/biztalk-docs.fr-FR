---
title: "Nouveauté de BizTalk Accelerator pour HL7 | Documents Microsoft"
description: "Modifications et mises à jour avec différentes versions de l’accélérateur HL7 dans BizTalk Server"
ms.custom: 
ms.date: 11/22/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e98595a1-2d1e-488e-8a97-7cd561948b3b
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3cdb992f749633bd517d6cad7f1acce926157c1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="whats-new-in-biztalk-accelerator-for-hl7"></a>Nouveautés de BizTalk Accelerator pour HL7
Modifications et mises à jour avec le [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)]. 

## <a name="biztalk-server-2016"></a>BizTalk Server 2016

|Fonctionnalité| Description|  
|---|---| 
| **Initie la connexion au cœur de métier** | À l’aide de l’adaptateur MLLP, [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] peut démarrer ou de la connexion à un système de serveur (LOB) Line of Business à distance. L’objet LOB attend que la connexion, puis envoie les messages à [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] à l’aide de l’adaptateur MLLP. Il existe certaines nouvelles propriétés dans le MLLP emplacement de réception que configurer cette option. Consultez : <br/><ul><li>[Étape 4 du didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)</li><li>[Étape 4 du didacticiel interrogative](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)</li><li>[Étape 5 du didacticiel interrogative](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)</li><li>[Étape 4 du didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)</li></ul>Dans [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures, le MLLP HL7 recevoir l’adaptateur attend que le serveur LOB à distance pour se connecter à l’adaptateur MLLP, puis envoie des messages dans le système métier. <br/><br/>Consultez [comment BTAHL7 route les messages](../../adapters-and-accelerators/accelerator-hl7/how-btahl7-routes-messages.md) pour plus d’informations.|

## <a name="biztalk-server-2013-r2"></a>BizTalk Server 2013 R2  
  
|Fonctionnalité| Description|  
|-------------|-----------------|  
|**prise en charge 64 bits**|Les adaptateurs MLLP et le pipeline HL7 peuvent exécuter dans les deux les instances d’hôte 32 bits et 64 bits.<br /><br /> Le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] installation inclut un package d’installation 32 bits et un package d’installation 64 bits. Sur un ordinateur 32 bits, installez uniquement le package 32 bits. Sur un ordinateur 64 bits, installez 32 bits **ou** package 64 bits. <br/><br/>**Important :** pour utiliser la prise en charge 64 bits, installer uniquement le package 64 bits. Le package 64 bits permet à l'adaptateur et aux pipelines de s'exécuter en mode 32 bits et 64 bits.|  
|**prise en charge du schéma v2.6**|La prise en charge inclut :<br /><br /> -   **BTAHL7V26Common** projet : inclut les schémas v2.6.<br />-   **BTAHL7Common** projet : inclut les schémas v2.6 et le schéma d’accusé de réception ACK_26_GLO_DEF ; ce qui génère l’accusé de réception pour les messages v2.6.<br />-   **MSH_25_GLO_DEF** schéma : Handles nouveaux qui sont inclus dans le schéma v2.6 et continue à prendre en charge v2 tous les champs d’en-tête de message. *x* schémas.|  
|**Prise en charge de l’adaptateur MLLP dynamique**|Port d’envoi de l’adaptateur de propriétés peuvent être configurées lors de l’exécution à l’aide d’un unidirectionnelle ou bidirectionnelle (requête-réponse). Consultez [adaptateur MLLP dynamique](../../adapters-and-accelerators/accelerator-hl7/dynamic-mllp-adapter.md).|  
|**Prise en charge « FreeText »**|Si un champ ou un segment est défini comme « FreeText », les données de caractères dans le champ/segment ne sont pas analysées. Consultez [l’encodage de caractères à l’aide de texte libre](../../adapters-and-accelerators/accelerator-hl7/encoding-characters-using-free-text.md).|  
|**MSH non valide dans les messages sont envoyés à un accusé de réception ou un accusé de réception négatif**|À l’aide de la **ReturnErrorForInvalidMSH3** clé de Registre, un accusé de réception négatif (NACK) est envoyé au tiers si les éléments suivants se produisent :<br /><br /> -MSH3 non valide (la partie n’est pas défini dans l’Explorateur de Configuration HL7) <br />    **AND**<br />-Les valeurs MSH15 et MSH16 dans le message sont null ou vide.<br /><br /> Pour envoyer l’accusé de réception négatif, la clé de Registre suivante la valeur 1, puis redémarrez l’instance d’hôte :<br /><br /> hôte 32 bits :`HKLM\SOFTWARE\Microsoft\BizTalk Accelerator for HL7`<br /><br /> hôte 64 bits :`HKLM\ SOFTWARE\Wow6432Node\Microsoft\BizTalk Accelerator for HL7` <br/><br/>**Conseil :** un port peut s’abonner au message ayant échoué : <ul><li>Utilisez le **BTAHL7Schemas.ParseError = True** condition de filtre.</li><li>Utilisez le **passer** pipeline.</li></ul>|  
|**Instance de message d’accusé de réception demeure actif**|En l’absence d’échec de la connexion au système en amont, l’accusé de réception (ACK) envoyé au système en amont est resté dans un état actif.<br /><br /> Nouveau comportement : En l’absence d’échec de la connexion au système en amont, le message d’accusé de réception est suspendu.|  
|**Ne pas envoyer \<SB\>**|Cette propriété est ajoutée pour les propriétés de configuration du port d’adaptateur de réception. Pour activer cette propriété, définissez la **UseMLLPTransACK** valeur :<br /><br /> -Lorsque la valeur **False** (valeur par défaut), l’adaptateur envoie le message si les données commencent par \<SB\>. Par exemple, le message suivant est envoyé :<br /> `<SB\>DataData<CR\>DataData<CR\>…`<br/><br />-Lorsque la valeur **True**, l’adaptateur envoie le message si les données sont manquantes \<SB\> au début. Par exemple, le message suivant est envoyé :<br /> `DataData<CR\>DataData<CR\>…` <br/><br/>**Important :** si un port d’envoi façon a **n’envoient pas \<SB\>**  définie sur True, il n’envoie pas service bus avec le message au système en aval. En même temps, il peut recevoir l’accusé de réception sans les service bus à partir du système en aval.|  
|**Accepter manquant \<SB\>**|Cette propriété est ajoutée aux propriétés de configuration de port de carte envoi. Pour activer cette propriété, définissez la **UseMLLPTransACK** valeur :<br /><br /> -Lorsque la valeur **False** (valeur par défaut), l’adaptateur retourne une erreur si les données sont manquantes \<SB\> au début. Par exemple, le message suivant retourne une erreur :<br /> `DataData<CR\>DataData<CR\>…`<br/><br />-Lorsque la valeur **True**, l’adaptateur peut recevoir le message si les données sont manquantes \<SB\> au début. Par exemple, les messages suivants sont reçus :<br /> `<SB\>DataData<CR\>DataData<CR\>…` <br />`DataData<CR\>DataData<CR\>…` <br/><br/>**Important :** si un port de réception bidirectionnel a **accepter manquant \<SB\>**  définie sur True, il n’acceptera le SB manquant dans le message du système en amont. En même temps n’est envoyé SB au système en amont.|  
  
## <a name="biztalk-server-2013"></a>BizTalk Server 2013  
  
 Les améliorations suivantes ont été incluses dans les versions précédentes :  
  
-   Récupérable échange prise en charge dans le pipeline de HL7 lot dans des scénario de lot.  
  
 La fonctionnalité suivante a été supprimée dans les versions précédentes :  
  
-   Fonctionnalité de suivi des activités de contrôle d’intégrité est supprimée de BizTalk Server et par conséquent, fonctionnalité d’audit est supprimée de BTAHL7 mais journalisation reste intacte.  
  
 La fonctionnalité suivante a été modifiée dans les versions précédentes :  
  
-   Le « service audit et journalisation » est renommé en tant que « Service de journalisation de HL7 ».  

## <a name="see-also"></a>Voir aussi

[Nouveautés de BizTalk Server 2016](../../install-and-config-guides/what-s-new-in-biztalk-server-2016.md)  
[Nouveautés de BizTalk Server 2013 R2 et 2013](../../install-and-config-guides/what-s-new-in-biztalk-server-2013-and-2013-r2.md)