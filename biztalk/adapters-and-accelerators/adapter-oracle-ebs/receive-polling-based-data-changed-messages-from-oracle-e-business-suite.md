---
title: "Recevoir des messages d’interrogation de données modifiées à partir d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbcb23d0-508d-4601-91b4-c674d76cd063
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aed2e9b42be9aaa44f1f79bf11da03d737dac4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-oracle-e-business-suite"></a>Recevoir des messages d’interrogation de données modifiées à partir d’Oracle E-Business Suite
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] prend en charge la réception des messages de modification de données reposant sur l’interrogation en interrogeant les tables d’interface, les vues de l’interface, les tables et les vues. L’adaptateur remet les messages à votre application par :  
  
-   Exécution d’une requête SQL SELECT pour déterminer si les données sont disponibles pour l’interrogation. Vous pouvez configurer l’adaptateur pour exécuter la requête SQL SELECT régulièrement ou en continu.  
  
-   Exécuter une requête SQL SELECT sur une table Oracle ou une vue ou procédures stockées, fonctions, ou empaquetées procédures et fonctions.  
  
-   Exécute un bloc de code après interrogation PL/SQL facultatif dans Oracle E-Business Suite. Ce bloc de code est souvent utilisé pour mettre à jour un champ sur les enregistrements interrogées dans la cible ou pour déplacer les enregistrements de requête vers une autre table ou vue.  
  
-   Retour des résultats de la requête dans un résultat défini en appelant l’opération d’interrogation ou les procédures stockées, fonctions, ou les procédures et fonctions qui sont exposées en tant que les opérations d’interrogation.  
  
 L’adaptateur s’exécute, toutes ces opérations à l’intérieur d’une transaction Oracle.  
  
## <a name="how-do-i-configure-the-oracle-e-business-adapter-for-receiving-data-changed-messages-using-binding-properties"></a>Comment configurer l’adaptateur Oracle E-Business pour recevoir des Messages de modification de données à l’aide des propriétés de liaison ?  
 Vous configurez le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données en définissant certaines ou toutes les propriétés suivantes de la liaison.  
  
|Propriété de liaison|Valeur|Valeur par défaut|Obligatoire/Facultatif|  
|----------------------|-----------|-------------|------------------------|  
|**InboundOperationType**|Assurez-vous que la valeur est définie sur **d’interrogation**.|Interrogation|Obligatoire. Si la valeur n’est pas explicitement ensemble, la valeur par défaut s’applique.|  
|**PolledDataAvailableStatement**|Spécifiez l’instruction SELECT est exécutée pour déterminer si les données sont disponibles pour l’interrogation d’une table spécifique. L’instruction spécifiée doit retourner un jeu de résultats composé de lignes et de colonnes. La valeur de la première cellule du jeu de résultats indique si l’adaptateur s’exécute à la valeur spécifiée pour le **PollingInput** propriété de liaison. Si la première cellule de résultat contient une valeur positive, l’adaptateur exécute l’instruction d’interrogation. Par exemple, une instruction valide pour cette propriété de liaison seront :<br /><br /> `Select * from <table_name>`<br /><br /> **Remarque :** vous ne devez pas spécifier des procédures stockées pour cette propriété de liaison. En outre, cette instruction ne doit pas modifier les données dans Oracle E-Business Suite ou de la base de données Oracle.|Null|Obligatoire.|  
|**PollingAction**|Spécifie l’action pour l’opération d’interrogation. Vous pouvez déterminer l’action de l’interrogation d’une opération spécifique à partir des métadonnées que vous générez pour l’opération en utilisant la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].|Null|Facultatif pour les opérations d’interrogation sur les tables et vues à l’aide de l’instruction SELECT.|  
|**PollingInput**|Spécifier un des éléments suivants :<br /><br /> -Instruction SQL SELECT qui doit être exécutée avec Oracle E-Business Suite. Cette instruction doit inclure une clause FOR UPDATE. Pour plus d’informations sur la clause FOR UPDATE, consultez [spécifiant une Clause de mise à jour pour dans l’instruction d’interrogation](#ForUpdate) plus loin dans cette rubrique.<br /><br /> -Message de demande pour une procédure stockée, fonction ou procédure ou une fonction dans un package que vous souhaitez interroger.|Null|Obligatoire. Paramètre **PollingInput** à une valeur non null permet d’interrogation.|  
|**PollingInterval**|Définir l’intervalle, en secondes, à laquelle vous souhaitez que l’adaptateur requête Oracle E-Business Suite. Cette propriété spécifie l’intervalle d’interrogation et le délai d’attente d’interrogation de transaction. La valeur doit être supérieure à la quantité de temps que nécessaire pour exécuter la requête et post-l’interrogation instruction (le cas échéant) sur Oracle E-Business Suite ainsi que la quantité de temps que nécessaire pour traiter les données de la requête et renvoyer le message de réponse d’interrogation au client.|30|Obligatoire. Si la valeur n’est pas explicitement ensemble, la valeur par défaut s’applique.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et interroge en permanence Oracle E-Business Suite, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié|False|Obligatoire. Si la valeur n’est pas explicitement ensemble, la valeur par défaut s’applique.|  
|**PostPollStatement**|Définir dans un bloc de code PL/SQL facultatif qui est exécuté par l’adaptateur, une fois que la requête est exécutée, mais avant que la requête les données sont retournées au client.|Null|Ce paramètre est facultatif. Si aucune valeur n’est spécifiée, une instruction de sondage post n’est pas exécutée.|  
  
> [!NOTE]
>  Si vous utilisez le modèle de service WCF ou le modèle de canal WCF, vous devez également définir le **AcceptCredentialsInUri** propriété de liaison.  
  
##  <a name="ForUpdate"></a>En spécifiant un pour mettre à jour les Clause dans l’instruction d’interrogation  
 Si vous utilisez une instruction SELECT en tant que l’instruction d’interrogation et l’exécution d’une instruction après interrogation qui affecte les lignes spécifiées dans l’instruction SELECT, vous devez utiliser la clause FOR UPDATE dans l’instruction d’interrogation. Vous spécifiez une clause FOR UPDATE permet de s’assurer que les enregistrements sélectionnés par l’instruction d’interrogation sont verrouillées lors de la transaction et que l’instruction après interrogation peut effectuer toutes les mises à jour requises sur les.  
  
> [!CAUTION]
>  Vous pouvez avoir des scénarios où, dans la fenêtre de temps entre les instructions après interrogation et d’interrogation, plusieurs enregistrements sont ajoutés à la table qui répondent à la condition de l’instruction après interrogation. Dans ce cas, l’instruction après interrogation serait mettre à jour tous les enregistrements qui satisfont la condition et pas seulement les enregistrements sélectionnés comme faisant partie de l’instruction d’interrogation.  
  
 Si une instruction après interrogation est spécifiée et que l’instruction d’interrogation ne contient pas une clause FOR UPDATE, vous rencontrez l’un des deux conditions suivantes :  
  
-   Si **TransactionIsolationLevel** a la valeur **ReadCommitted**, la requête d’interrogation après ne met pas à jour les lignes sélectionnées.  
  
-   Si **TransactionIsolationLevel** a la valeur **Serializable**, suivantes ciblent exception système (**Microsoft.ServiceModel.Channels.Common.TargetSystemException**) se produit lors de l’exécution de l’instruction après interrogation : « ORA-08177 ne peut pas sérialiser l’accès pour cette transaction ». Dans ce cas, vous devez définir le **PollingRetryCount** liaison de propriété pour définir le nombre de fois où vous souhaitez que l’adaptateur pour retenter la même transaction.  
  
 Pour obtenir des instructions sur la façon de définir le niveau d’isolation de transaction, consultez [configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  
  
 Les instructions après interrogation et d’interrogation sont exécutées dans une transaction si les clients de la carte ont configuré pour utiliser des transactions et la valeur de la **UseAmbientTransaction** liaison de la propriété est définie sur **True**dans l’adaptateur.  
  
 Est un exemple d’une requête d’interrogation avec l’option de mise à jour :  
  
```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE  
```  
  
### <a name="specifying-a-nowait-clause-in-the-polling-statement"></a>Spécification d’une Clause NOWAIT dans l’instruction d’interrogation  
 Vous pouvez avoir des scénarios où des threads simultanés accèdent à la table interrogée, conduisant à un trop grand nombre de conflits dans la table. Cela peut entraîner la requête d’interrogation peut être bloqué pour obtenir un verrou sur les lignes de la table. Si vous utilisez une instruction SELECT en tant que l’instruction d’interrogation, il pouvez que vous souhaitez spécifier un mot-clé NOWAIT, ainsi que le mot clé pour la mise à jour dans l’instruction SELECT. Cela entraîne l’exécution de la requête d’interrogation de l’adaptateur pour retourner immédiatement s’il existe des verrous sur les lignes dont la requête d’interrogation est une tentative de sélection. Une exception est généralement levée par Oracle dans ces conditions. Là encore, les clients de l’adaptateur peuvent utiliser le **PollingInterval** propriété pour spécifier l’intervalle de temps après lequel les clients de l’adaptateur doivent Réessayer afin d’interroger les données de liaison.  
  
 Un exemple d’une requête d’interrogation avec l’option NOWAIT est :  
  
```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE NOWAIT  
```  
  
### <a name="specifying-a-skip-locked-clause-in-the-polling-statement"></a>Spécifier une Clause de verrouillé SKIP dans une instruction d’interrogation  
 Vous pouvez avoir des scénarios où certaines lignes du jeu de résultats de la clause WHERE spécifiée dans la requête d’interrogation en raison de l’accès à la table interrogée de threads simultanés, verrouillés. Par exemple, votre requête d’interrogation retourne des 6 lignes à partir d’une table ; 4 en dehors de ces 6 lignes sont déjà verrouillés en raison d’une autre transaction. Dans ce cas, vous souhaiterez spécifier un mot-clé ignorer verrouillés en même temps que le mot clé pour la mise à jour qui fait en sorte que la base de données tente de verrouiller les lignes spécifiées par la clause WHERE et pour ignorer toutes les lignes qui sont trouvent le point d’être déjà verrouillé. Les lignes non verrouillées dans la clause WHERE sont verrouillées pendant la transaction et l’instruction après interrogation peut effectuer toutes les mises à jour requises sur ces afin que ces lignes ne sont pas interrogés à nouveau. Cela garantit que vous n’avez pas à attendre de recevoir les messages d’interrogation jusqu'à ce que toutes les lignes spécifiées par la clause WHERE sont déverrouillées.  
  
 Le mot clé SKIP verrouillé est utile dans un scénario où vous avez des clients de l’adaptateur sur plusieurs ordinateurs qui demandent la même table dans une base de données. Vous pouvez charger l’équilibre entre les clients de la carte en configurant l’opération d’interrogation de manière à ce que vous recevez des messages de modification de données reposant sur l’interrogation pour les lignes spécifiées par la clause WHERE qui ne sont pas verrouillées pour le moment d’exécution et ensuite mettre à jour la ligne pour vous assurer que si un message de modification de données reposant sur l’interrogation est reçu par un client de carte, les autres clients n’obtiennent pas le même message.  
  
 Est un exemple d’une requête d’interrogation avec l’option SKIP verrouillé :  
  
```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE SKIP LOCKED  
```  
  
## <a name="support-for-ordered-delivery-fifo"></a>Prise en charge de la livraison chronologique des messages (FIFO)  
 Dans un environnement de production, l’interrogation peut être utilisée pour surveiller les modifications de données dans Oracle E-Business Suite. Ces messages de modification de données sont reçus par le client de carte à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Selon les scénarios d’entreprise, il peut être essentiel que les messages de modification de données sont reçus par le client de l’adaptateur dans le bon ordre.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge classés de remise ou in-first-out (FIFO) pour conserver l’ordre dans lequel les messages sont reçus à partir d’Oracle E-Business Suite. Voici quelques considérations liées à la prise en charge de FIFO dans les scénarios de trafic entrants pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
-   Si le message est consommé par une orchestration, l’orchestration doit avoir la livraison chronologique des messages défini pour les messages en provenance de le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] port de réception.  
  
-   Si le message est consommé par un scénario de port (dans un routage basé sur le contenu) d’envoi, le port d’envoi doit avoir livraison chronologique des messages défini pour les messages en provenance de le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] port de réception.  
  
 L’adaptateur WCF-Custom ou WCF-OracleEBS possède une propriété **suspendre le message de demande en cas d’échec** qui spécifie s’il faut interrompre le message de demande que le traitement entrant a échoué. Cette propriété peut être définie sur le **Messages** onglet du WCF-Custom ou WCF-OracleEBS réception port sous la **la gestion des erreurs** section. Le tableau suivant répertorie les scénarios décrivant la façon dont les messages entrants sont traités en fonction de si cette propriété est définie et l’état de l’abonné de message (orchestration ou port).  
  
|Propriété du port WCF-Custom|Abonné dans un état désinscrit|Abonné dans inscrite, mais l’état arrêté|  
|-------------------------------|------------------------------------|----------------------------------------------|  
|**Suspendre le message de demande en cas d’échec** propriété non définie|-Rapport d’échec routage est généré comme interrompue (sans reprise possible)<br /><br /> -Réel du message n’est pas interrompu.<br /><br /> -Requête d’interrogation n’est pas exécutée lorsque la transaction est interrompue. Par conséquent, l’interrogation se répète et extrait les lignes à nouveau.<br /><br /> -Erreurs signalées dans l’événement journal de décrire ce qui s’est produit.|-N’est pas considéré comme un « échec ». Il existe des messages d’erreur dans le journal des événements.<br /><br /> -Message réel est placé dans la file d’attente suspendue (peut être repris).<br /><br /> -Lorsque le port ou une orchestration abonnée démarre, les messages sont automatiquement repris. Si la livraison chronologique des messages sont défini sur l’abonné, elle est respectée.<br /><br /> -Les messages peuvent également être repris manuellement.|  
|**Suspendre le message de demande en cas d’échec** est définie|-Rapport d’échec routage est généré comme interrompue (sans reprise possible)<br /><br /> -Réel du message est également interrompu.<br /><br /> -Requête d’interrogation n’est pas exécutée lorsque la transaction est interrompue. Par conséquent, l’interrogation se répète et extrait les lignes à nouveau.<br /><br /> -Erreurs signalées dans l’événement journal de décrire ce qui s’est produit.|-N’est pas considéré comme un « échec ». Il existe des messages d’erreur dans le journal des événements.<br /><br /> -Message réel est placé dans la file d’attente suspendue (peut être repris).<br /><br /> -Lorsque le port ou une orchestration abonnée démarre, les messages sont automatiquement repris. Si la livraison chronologique des messages sont défini sur l’abonné, elle est respectée.<br /><br /> -Les messages peuvent également être repris manuellement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Activités de développement](../../esb-toolkit/development-activities.md)   
 [Interrogation Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)