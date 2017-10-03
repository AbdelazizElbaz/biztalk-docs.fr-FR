---
title: "Utilisez l’adaptateur de base de données Oracle avec SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254204e5-3b5d-4e70-97ab-817660d1206a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cf5be42a008cadba648739037797160386a42fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-the-oracle-database-adapter-with-sharepoint"></a>Utilisez l’adaptateur de base de données Oracle avec SharePoint
L’Assistant de développement de services de l’adaptateur WCF pour [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] permet à l’adaptateur Microsoft BizTalk pour base de données Oracle et l’adaptateur Microsoft BizTalk pour Oracle E-Business Suite être utilisés directement comme une source de données externe dans Microsoft SharePoint. L’Assistant Ajout de développement Service qui prend en charge cette fonctionnalité est lancé avec le **Service d’adaptateur WCF** modèle pour créer un nouveau Visual C# Sites Web dans [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]. Le modèle est inclus avec le [!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)]. Vous devez également installer le SDK de l’adaptateur de métier (LOB) de Microsoft Windows Communication Foundation (WCF).  
  
## <a name="sharepoint-operation-support"></a>Prise en charge de SharePoint opération  
 L’Assistant de développement de services de l’adaptateur génère un contrat de service spéciales pour les adaptateurs Oracle qui est compatible avec Microsoft SharePoint. L’Assistant génère un contrat de service qui inclut les opérations suivantes pour l’intégration de l’adaptateur avec Microsoft SharePoint :  
  
-   **Créer :** pris en charge par l’opération CreateItem_.  
  
-   **Lecture :** pris en charge par l’opération ReadItem_.  
  
-   **Mise à jour :** pris en charge par l’opération UpdateItem_.  
  
-   **Suppression :** pris en charge par l’opération DeleteItem_.  
  
-   **Requête :** pris en charge par l’opération ReadList.  
  
-   **Associer :** pris en charge par l’opération Associate_.  
  
 Le contrat de service suivant a été généré à l’aide de l’adaptateur Microsoft BizTalk pour base de données Oracle par exemple. L’adaptateur est configuré pour fournir un accès à la table EMP  
  
```  
[System.ServiceModel.ServiceContractAttribute()]  
public interface ISCOTT_EMP {  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadList(System.Nullable<int> Limit);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void CreateItem(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void UpdateItem_EMPNO(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void DeleteItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] Associate_DEPTNO(System.Nullable<decimal> DEPTNO);  
}  
```  
  
## <a name="creating-a-new-web-site-to-host-the-microsoft-biztalk-adapter-for-oracle-database-in-iis"></a>Création d’un Site Web pour héberger l’adaptateur Microsoft BizTalk pour base de données Oracle dans IIS  
 Ces étapes fournissent un exemple d’utilisation de l’Assistant de développement Service de l’adaptateur WCF, pour créer un service web WCF hébergeant l’adaptateur Microsoft BizTalk pour base de données Oracle. Le contrat de service inclut des opérations directement compatibles avec Sharepoint. Afin que celles-ci peuvent être directement consommées comme une source de données externe. L’adaptateur est configuré pour s’authentifier auprès de la base de données Oracle à l’aide du **SCOTT** compte. Si le **SCOTT** compte est verrouillé, vous pouvez déverrouiller le compte en vous connectant à SQL Plus tant que SYSDBA.  
  
```  
<Oracle Installation Bin Directory>\Sqlplus.exe SYS AS SYSDBA  
```  
  
 Puis exécutez la commande suivante.  
  
```  
SQL> ALTER USER scott ACCOUNT UNLOCK;  
```  
  
#### <a name="creating-the-new-web-site-project"></a>Création du nouveau projet de Site Web  
  
1.  Démarrer **Microsoft [!INCLUDE[vs2012](../../includes/vs2012-md.md)]** .  
  
2.  Dans [!INCLUDE[vs2010](../../includes/vs2010-md.md)], dans le **fichier** menu, sélectionnez **nouveau** puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez **autres langages** et cliquez sur **Visual C#**. Rechercher les **Service d’adaptateur WCF** dans le modèle de liste et cliquez dessus pour le sélectionner.  
  
    > [!NOTE]
    >  Le **Service d’adaptateur WCF** modèle n’est pas disponible si le [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)] n’est pas installé. Sur x64 systèmes, installez les versions x86 et x64 de la [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)].  
  
4.  Spécifiez **ScottEMP** pour le nom, puis cliquez sur **OK**. Le **Assistant développement d’adaptateurs WCF** démarre.  
  
5.  Sur le **Introduction** , cliquez sur **suivant**.  
  
6.  Sur le **choisissez les opérations** , spécifiez la **oracleDBBinding** liaison.  
  
7.  Cliquez sur le **configurer** bouton. Le **configurer l’adaptateur** boîte de dialogue s’affiche.  
  
8.  Sur le **sécurité** onglet, sélectionnez **nom d’utilisateur** dans les **type d’informations d’identification du Client** zone de liste déroulante.  
  
9. Entrez **SCOTT** pour l’utilisateur de nom et entrez le mot de passe du compte SCOTT. Le mot de passe pour le compte SCOTT **tiger**.  
  
10. Cliquez sur le **propriétés URI** , entrez le nom d’hôte ou adresse IP de votre serveur Oracle dans la **ServerAddress** boîte.  
  
11. Entrez le nom d’instance correct des service de base de données Oracle dans la **ServiceName** boîte. Vous pouvez copier les informations de nom d’instance à partir d’Oracle Enterprise Manager.  
  
12. Appuyez sur la **OK** bouton sur le **configurer l’adaptateur** boîte de dialogue  
  
13. Sur le **choisissez les opérations** page de l’Assistant, cliquez sur le **Connect** bouton et attendez quelques instants pour les catégories à générer pour la base de données Oracle.  
  
14. Une fois que les catégories sont ajoutés dans le **sélectionner une catégorie** liste, faites défiler jusqu'à **SCOTT** et développez-le. Puis développez **Table** et cliquez sur le **EMP** entrée de la table.  
  
15. Dans le **catégories et opérations disponibles** , sélectionnez toutes les opérations dans la liste et cliquez sur le **ajouter** bouton. Toutes les opérations sont ajoutées à la **ajouté des catégories et opérations** liste.  
  
16. Sur le **choisissez les opérations** , cliquez sur le **suivant** bouton.  
  
17. Sur le **configurer le Service et les comportements de point de terminaison** , définissez le **UseServiceCertificate** comportement de Service **false** pour cet exemple. Puis cliquez sur le **suivant** bouton.  
  
18. Sur le **configurer la liaison de point de terminaison de Service et l’adresse** , cliquez sur le **appliquer** bouton. Puis cliquez sur le **suivant** bouton.  
  
19. Sur le **Résumé** , cliquez sur le **Terminer** bouton.  
  
20. Cliquez sur le **générer** option de menu, puis cliquez sur **générer la Solution**. Vérifiez que la génération du projet a réussi sans erreurs.  
  
## <a name="publishing-the-new-service-to-iis"></a>Le nouveau Service de publication sur le serveur IIS  
 Pour cet exemple, vous allez publier le service hôte de l’adaptateur au serveur web IIS local.  
  
1.  Dans l’Explorateur de solutions pour [!INCLUDE[vs2010](../../includes/vs2010-md.md)], bouton droit sur le **ScottEmp** projet puis cliquez sur **propriétés**. Les onglets du Concepteur de projet sont affichés.  
  
2.  Cliquez sur le **Web** onglet, puis cliquez sur le **serveur Web IIS Local d’utilisation** option.  
  
3.  Cliquez sur le **créer un répertoire virtuel** bouton.  
  
4.  Ouvrez un navigateur web à l’adresse du service **http://localhost/ScottEmp/ISCOTT_EMP.svc**. Vous devez recevoir un message indiquant « Vous avez créé un service » indiquant l’adaptateur est hébergé dans IIS.  
  
## <a name="adding-the-external-data-source-to-a-sharepoint-site-using-sharepoint-designer"></a>Ajout de la Source de données externe sur un SharePoint Site à l’aide de SharePoint Designer  
 Cette section décrit comment ajouter le Service WCF en tant que source de données externe à un nouveau Site Web à l’aide de SharePoint Designer.  
  
#### <a name="adding-the-external-data-source"></a>Ajout de la source de données externes  
  
1.  Ouvrez SharePoint Designer et créer un nouveau Site Web.  
  
2.  Dans SharePoint Designer, développez **Navigation** et cliquez sur **types de contenu externe** dans les **objets du Site** liste.  
  
3.  Cliquez sur le **le Type de contenu externe** bouton de menu pour créer un nouveau type de contenu externe.  
  
4.  Cliquez sur le texte en regard de **nom** pour modifier le nom du nouveau type de contenu externe. Entrez **OracleEMP** pour le nom.  
  
5.  Cliquez sur le lien de texte en regard de **système externe** selon **cliquez ici pour découvrir les sources de données externes et les opérations.**. Le Concepteur de l’opération pour le type de contenu externe OracleEMP s’ouvre.  
  
6.  Cliquez sur le **ajouter une connexion** bouton sur l’écran de découverte.  
  
7.  Dans la boîte de dialogue Sélection de Type de Source de données externe, choisissez **Service WCF** et cliquez sur le **OK** bouton.  
  
8.  Dans la boîte de dialogue de connexion de WCF, dans le **URL des métadonnées de Service** , saisissez **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**  
  
9. Dans le **URL de point de terminaison de Service** , saisissez **https://localhost/ScottEmp/ISCOTT_EMP.svc**  
  
10. Cliquez sur le **OK** pour fermer la boîte de dialogue de connexion de WCF.  
  
11. Une fois que les informations de Source de données sont remplies, développez le **https://localhost/ScottEmp/ISCOTT_EMP.svc** source de données et développez **méthodes Web**.  
  
12. Bouton droit sur le **ReadList** méthode Web et cliquez sur **nouvelle opération de liste en lecture**. La boîte de dialogue de configuration de liste en lecture est lancé.  
  
13. Dans la boîte de dialogue liste de lecture, cliquez sur **paramètres de retour** et cliquez sur **MATEMP** dans les éléments de Source de données. Cliquez sur le **carte à identificateur**.  
  
14. Cliquez sur **Terminer** dans la boîte de dialogue liste de lecture.  
  
15. Enregistrer la nouvelle source de données externe en tapant **Ctrl + s**.  
  
#### <a name="testing-the-external-data-source-connection"></a>Test de la connexion de Source de données externes  
  
1.  Dans le nouveau site web, cliquez sur le **créer des listes et des formulaires** bouton. Le formulaire de boîte de dialogue OracleEMP et de créer une liste apparaît.  
  
2.  Entrez **OracleEMP_List** pour le nom de la liste et cliquez sur le **OK** bouton.  
  
3.  Une fois que la liste est créé, cliquez sur le **mode Résumé** bouton dans le menu.  
  
4.  Cliquez sur **OracleEMP_List** sous listes externes.  
  
5.  Cliquez sur le **Aperçu dans le navigateur** bouton dans le menu pour tester l’opération ReadList de la carte.  
  
## <a name="troubleshooting"></a>Dépannage  
  
-   Sur les ordinateurs 64 bits, il se peut que vous devez vous assurer que les composants du client Oracle 32 bits sont également installées. C’est parce que [!INCLUDE[vs2010](../../includes/vs2010-md.md)] et exécute ses Assistants comme un processus 32 bits qui demande l’accès à des composants 32 bits pendant le développement.