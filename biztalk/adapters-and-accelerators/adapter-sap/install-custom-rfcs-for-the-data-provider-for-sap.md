---
title: Installez les RFC personnalisés pour le fournisseur de données pour SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation, custom RFCs for the Data Provider for SAP
- installing, custom RFCs for the Data Provider for SAP
- installing custom RFCs, how to
ms.assetid: 7a99db70-fa5a-4c04-9dc7-b71613d4364e
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0aff501e5bf59d6ae22d9ad2a00e0e5ff5ad4605
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="install-custom-rfcs-for-the-data-provider-for-sap"></a>Installez les RFC personnalisés pour le fournisseur de données pour SAP
Installez les RFC personnalisés si vous souhaitez utiliser le fournisseur de données .NET Framework pour mySAP Business Suite pour accéder au système SAP.

Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert les RFC personnalisés à effectuer certaines opérations sur le système SAP pour :
  
-   Exécuter l’opération de sélection, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert Z_EXTRACT_DATA_OO RFC.  
  
-   Exécutez l’opération EXECQUERY, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert Z_EXECUTE_SAP_QUERY RFC.  
  
Pour effectuer ces opérations sur le système SAP, vous devez installer ces RFC personnalisés sur le système SAP. Si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], le programme d’installation copie le transport RFC pour les [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] comme un fichier compressé (customRFC.zip) sur le système sur lequel vous installez l’adaptateur. Le fichier zip est généralement installé sur  *\<lecteur d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft .NET Framework Data Provider pour mySAP Business Suite*. 
  
 Après avoir extrait le fichier zip, vous trouverez les quatre fichiers de données, deux après l’attribution de noms de modèle K9 *. BI1 (par exemple, semblable à K900534. BI1) et les deux autres suivant le modèle R9\*. BI1 (par exemple, semblable à R900534. BI1).  
  

  
1.  Copiez les fichiers extraits à partir de l’ordinateur qui exécute les adaptateurs au serveur d’applications SAP.  
  
    1.  Ouvrez une session en tant que l’administrateur du système SAP r/3 au serveur d’applications SAP de votre système de développement.  
  
    2.  Copiez les fichiers de deux transport avec le modèle d’affectation de noms K9 *. BI1 du répertoire d’installation sur l’ordinateur qui exécute les adaptateurs dans le répertoire suivant sur le serveur d’applications SAP :  
  
         `<drive>:\usr\sap\trans\cofiles`  
  
    3.  Copiez les fichiers de deux transport avec le modèle d’affectation de noms R9 *. BI1 du répertoire d’installation sur l’ordinateur qui exécute les adaptateurs dans le répertoire suivant sur le serveur d’applications SAP :  
  
         `<drive>:\usr\sap\trans\data`  
  
2.  Chargez le transport dans la mémoire tampon de transport sur le serveur d’applications SAP.  
  
    1.  À l’invite de commandes, accédez au répertoire de programme de transport sur le serveur d’applications SAP :  
  
         `<drive>:\usr\sap\trans\bin`  
  
    2.  Pour charger le transport dans la mémoire tampon de transport, exécutez la commande suivante à la `\usr\sap\trans\bin` active et remplacer *sysid* avec l’ID système de votre système de développement :  
  
        ```  
        tp addtobuffer <TransportNumber> <sysid> pf=TP_DOMAIN_<sysid>.PFL  
        ```  
  
         WHERE, *TransportNumber* est le nombre réel de transport (par exemple BI1K900534).  
  
    3.  Après le `tp` commande terminée, vous verrez un rapport similaire à la suivante :  
  
        ```  
        This is tp version 320.56.66 (release 620)  
        Addtobuffer successful for TransportNumber  
        tp finished with return code: 0  
        ```  
  
         Code de retour « 0 » signifie que l’opération a réussi.  
  
         Un code de retour de 0 ou 4 est acceptable. Contactez le Service clientèle Microsoft et la prise en charge, si vous recevez un code de retour de 8 ou version ultérieure.  
  
        > [!IMPORTANT]
        >  Répétez les étapes (b) et (c) pour le deuxième ensemble de fichiers de transport.  
  
        > [!NOTE]
        >  Vous pouvez facilement déterminer le nombre réel de transport à partir du nom de fichier cofile. Par exemple, un cofile nommé K900534. BI1 fournit un nombre de transport de BI1K900534.  
  
3.  Importer le transport SAP.  
  
    1.  Exécutez la commande suivante à l’invite de commandes :  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL  
        ```  
  
         Remplacez *sysid* avec l’ID système de votre système de développement. Remplacez *clientnumber* avec le nombre de clients de votre système de développement.  
  
         Vous pouvez utiliser le paramètre U2 pour remplacer des objets précédemment installés, comme suit :  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> U2  
        ```  
  
         ou  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL U2  
        ```  
  
        > [!NOTE]
        >  Vous pouvez facilement déterminer le nombre réel de transport à partir du nom de fichier cofile. Par exemple, un cofile nommé K900534. BI1 fournit un nombre de transport de BI1K900534.  
  
    2.  Après le `tp` commande terminée, vous verrez un rapport similaire à la suivante :  
  
        ```  
        This is tp version 320.56.66 (release 620)  
        This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
        R3trans.exe finished (0000).  
        This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
        R3trans.exe finished (0000).  
        tp finished with return code: 0  
        ```  
  
         Code de retour « 0 » signifie que l’opération a réussi.  
  
         Un code de retour de 0 ou 4 est acceptable. Si vous recevez un code de retour de 8 ou version ultérieure, contactez le support technique et Service clientèle Microsoft.  
  
        > [!IMPORTANT]
        >  Répétez les étapes (a) et (b) pour le deuxième ensemble de fichiers de transport.  
  
4.  Vérifiez le journal de transport.  
  
5.  Vérifiez le journal de transport dans l’organisateur de Transport d’interface utilisateur graphique SAP à l’aide de la transaction SE09 pour vérifier qu’il n’y a aucune erreur.  
  
 Paramètre d’autorisation de l’utilisateur  
 Le document RFC Z_EXTRACT_DATA_OO requiert l’ID d’utilisateur avec des objets d’autorisation spécifique. Utilisez les outils d’administration de l’interface graphique utilisateur SAP d’autorisation pour définir les restrictions minimales sur l’exécution de la RFC :  
  
> [!NOTE]
>  Vous n’avez pas besoin définir l’autorisation pour le document RFC Z_EXECUTE_SAP_QUERY.  
  
-   Z_EXTRACT_DATA_OO requiert S_TABU_DIS et Z_EIP_TABL. Les valeurs suivantes fournissent les restrictions minimales pour S_TABU_DIS, qui permettent aux utilisateurs d’afficher les métadonnées pour n’importe quelle table dans le système.  
  
    -   ACTVT : 03  
  
    -   DICBERCLS : *  
  
     Vous pouvez utiliser DICBERCLS pour restreindre l’autorisation aux tables par classe d’autorisation.  
  
     Vous pouvez utiliser le tableau TDDAT pour afficher la classe d’autorisation pour les tables.  
  
    > [!NOTE]
    >  Pour empêcher les modifications aux tables par les transactions de maintenance de table, vous ne devez octroyer des privilèges d’affichage dans un environnement de production (ACTVT : 03 définit l’activité autorisée à afficher).  
  
     Les valeurs minimales pour Z_EIP_TABL sont :  
  
    -   ACTVT : 03  
  
    -   TABLE : *  
  
     Vous pouvez utiliser la TABLE pour définir explicitement les tables autorisés. Notez que S_TABU_DIS est également utilisée dans d’autres transactions.  
  
##### <a name="to-set-user-authorization"></a>Pour définir l’autorisation de l’utilisateur  
  
1.  Démarrez l’interface utilisateur graphique SAP. Atteindre le code T, type `pfcg`, puis appuyez sur ENTRÉE.  
  
2.  Dans le **rôle** texte, entrez un nom de rôle que vous souhaitez créer, par exemple, `ZTEST`, puis cliquez sur **rôle**.  
  
3.  Dans le **Create Role** , cliquez sur le **autorisations** onglet.  
  
     Si vous êtes invité à enregistrer le rôle, cliquez sur **Oui**.  
  
4.  Dans le **modifier les rôles** , cliquez sur le **modifier les données d’autorisation** bouton.  
  
5.  Si vous êtes invité à sélectionner un modèle à partir de la **choisir un modèle** boîte de dialogue, cliquez sur **ne sélectionnez pas de modèles**.  
  
6.  Dans le **modification du rôle : autorisations** , cliquez sur le **manuellement** bouton.  
  
7.  Dans le **sélection manuelle des autorisations** , entrez le nom de l’objet d’autorisation `Z_EIP_TABL` et appuyez sur ENTRÉE.  
  
8.  Dans le **modification du rôle : autorisations** page, développez les nœuds jusqu'à ce que les zones de texte pour **activité** et **nom de la Table**. Pour le **activité** texte, entrez la valeur `03`. Pour le **nom de la Table** texte, entrez la valeur `*`.  
  
9. Cliquez sur le **enregistrer** bouton pour générer le profil.  
  
10. Revenez à la **modifier les rôles** page, puis cliquez sur le **utilisateur** onglet.  
  
11. Dans le **utilisateur** onglet, affectez un ID utilisateur pour le rôle en entrant le nom d’utilisateur dans le **ID utilisateur** colonne, puis cliquez sur le **comparaison de l’utilisateur** bouton.  
  
12. Dans le **comparer un enregistrement de rôle d’utilisateur principal**, cliquez sur **effectuer la comparaison** pour mettre à jour l’enregistrement principal. Lorsque vous êtes invité à enregistrer le rôle, cliquez sur **Oui**.  
  
13. Enregistrez et quittez.  
  
Vérification de l’Installation de la RFC personnalisés  
 Après avoir installé les RFC personnalisés, vous pouvez vérifier si les documents RFC a été installé correctement.  
  
-   Pour les RFC Z_EXECUTE_SAP_QUERY, vous pouvez le faire en exécutant une requête prédéfinie à l’aide du système SAP le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
-   Pour Z_EXTRACT_DATA_OO RFC, vous pouvez le faire en effectuant les tests suivants pour vérifier que le document RFC fonctionne et est prêt à être utilisé dans votre système.  
  
##### <a name="to-test-the-installation-of-zextractdataoo"></a>Pour tester l’installation de Z_EXTRACT_DATA_OO  
  
1.  Dans les outils d’administration d’autorisation interface GUI SAP, exécutez SE37, le module de fonction Z_EXTRACT_DATA_OO, et puis exécutez la RFC en mode test en appuyant sur `F8`. Remplir les paramètres comme suit.  
  
    |||  
    |-|-|  
    |IN_METADATA_ONLY||  
    |IN_METADATA_LANGUAGE|EN|  
    |IN_FROM_TABLE|T000|  
    |IN_OUTPUT_MODE|S|  
    |IN_OUTPUT_FILENAME||  
    |IN_USE_FIELD_EXITS|X|  
    |IN_SET_ROWCOUNT|0|  
    |IN_DELIMITER||  
    |IN_PACKET_SIZE|50,000|  
    |IN_MAX_WRITE_ATTEMPTS|4|  
    |IN_RETRY_DELAY|30|  
    |IN_SQL_DATES_ON||  
  
2.  Cliquez sur **Execute** ou appuyez sur `F8`.  
  
3.  Dans le volet de résultats, vérifiez les points suivants.  
  
    |||  
    |-|-|  
    |OUT_TABLEHEADER|\<Métadonnées générales T000\>|  
    |OUT_TECHNICALSETTINGS|\<Métadonnées de niveau de base de données techniques T000\>|  
    |OUT_RECORDLENGTH|\<varie selon la version SAP\>|  
    |OUT_RECORDCOUNT|\<Vérifiez le nombre de clients dans votre système avec SE16 sur T000\>|  
    |OUT_ZDATATABLE|\<vérifier ce résultat avec les données sources à l’aide de SE 16 sur T000\>|  
    |OUT_RETURN_TAB|S 001 réussite|  
  
## <a name="remove-the-rfc-for-the-data-provider-for-sap"></a>Supprimer la demande de changement pour le fournisseur de données pour SAP  
  
1.  Dans le navigateur d’objet interface utilisateur graphique SAP (SE80), rechercher tous les objets avec la classe de développement ZMSBI.  
  
2.  Supprimer tous les objets avec la classe de développement ZMSBI les dossiers d’objets suivants :  
  
    -   Structures  
  
    -   Groupes de fonctions  
  
    -   Objet autorisé  
  
3.  Déclencher un transport et migrez-le à chaque système où vous avez installé une commande RFC (développement, test et production systèmes, par exemple).  
  
     Pour obtenir une assistance, contactez votre administrateur de base de SAP.  
     
## <a name="next"></a>Suivant
[Présentation de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)  
[Didacticiels sur l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)