
# Spring Boot CRUD API - Gestion de Personnes

Une API RESTful complète pour la gestion de personnes, développée avec Spring Boot et JPA/Hibernate.

## Technologies utilisées

- Java 17
- Spring Boot 4.0.3
- Spring Data JPA (Hibernate)
- Spring Web MVC
- Base de données H2 (développement) / MySQL (production)
- Maven (gestion de dépendances)
- Git (versionnement)

Prérequis

- Java 17
- Maven 3.6+
- Git (optionnel)
- Un IDE IntelliJ

 Installation et exécution

1. Cloner le projet
git clone https://github.com/jean-leonkabobi/crud_springboot.git
cd crud_springboot

 2. Configuration de la base de données
Par défaut, l'application utilise H2 (base de données en mémoire).  
Pour changer, modifiez `src/main/resources/application.properties` :

properties
# Pour H2 (développement)
spring.datasource.url=jdbc:h2:mem:persondb
spring.datasource.driverClassName=org.h2.Driver
spring.h2.console.enabled=true

 Pour MySQL (production)
 spring.datasource.url=jdbc:mysql://localhost:3306/persondb
 spring.datasource.username=votre_username
 spring.datasource.password=votre_password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

3. Compiler et lancer l'application
 Avec Maven
./mvnw spring-boot:run

 Ou avec Maven installé globalement
mvn spring-boot:run

L'application démarrera sur `http://localhost:8080`

 Documentation de l'API

Endpoints disponibles

| Méthode | URL | Description | Corps de la requête |
|---------|-----|-------------|---------------------|
| GET | `/api/persons` | Récupérer toutes les personnes | - |
| GET | `/api/persons/{id}` | Récupérer une personne par ID | - |
| POST | `/api/persons` | Créer une nouvelle personne | JSON |
| PUT | `/api/persons/{id}` | Mettre à jour une personne | JSON |
| DELETE | `/api/persons/{id}` | Supprimer une personne | - |

Modèle de données (Person)

json
{
  "id": 1,
  "name": "Jean Dupont",
  "city": "Paris",
  "phoneNumber": "0123456789"
}


Exemples d'utilisation

 1. Créer une personne
curl -X POST http://localhost:8080/api/persons \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Jean Dupont",
    "city": "Paris",
    "phoneNumber": "0123456789"
  }'

Réponse (201 Created) :
{
  "id": 1,
  "name": "Jean Dupont",
  "city": "Paris",
  "phoneNumber": "0123456789"
}

2. Récupérer toutes les personnes
curl http://localhost:8080/api/persons

 3. Récupérer une personne par ID
curl http://localhost:8080/api/persons/1

 4. Mettre à jour une personne
curl -X PUT http://localhost:8080/api/persons/1 \
  -H "Content-Type: application/json" \
  -d '{
    "city": "Lyon",
    "phoneNumber": "0987654321"
  }'

 5. Supprimer une personne
curl -X DELETE http://localhost:8080/api/persons/1

 Structure du projet


crud_springboot/
├── src/
│   ├── main/
│   │   ├── java/com/jlk/crud_springboot/
│   │   │   ├── Person.java                 # Entité JPA
│   │   │   ├── PersonRepository.java        # Repository Spring Data
│   │   │   ├── PersonController.java        # Contrôleur REST
│   │   │   └── CrudSpringbootApplication.java # Classe principale
│   │   └── resources/
│   │       ├── application.properties       # Configuration
│   │       └── static/                       # Ressources statiques
│   └── test/                                 # Tests unitaires
├── pom.xml                                    # Dépendances Maven
├── mvnw                                       # Wrapper Maven
├── mvnw.cmd                                   # Wrapper Maven (Windows)
└── README.md                                  # Documentation


Améliorations possibles

- [ ] Ajouter la validation des données (`@Valid`, `@NotBlank`, etc.)
- [ ] Implémenter la pagination pour `GET /api/persons`
- [ ] Ajouter des DTO (Data Transfer Objects)
- [ ] Intégrer Swagger/OpenAPI pour la documentation automatique
- [ ] Ajouter des tests unitaires et d'intégration
- [ ] Gérer les exceptions avec `@ControllerAdvice`
- [ ] Ajouter une couche Service entre Controller et Repository

 Auteur

Jean-Leon Kabobi
- GitHub : [@jean-leonkabobi](https://github.com/jean-leonkabobi)
- Gmail : jeanleon.kabobi@gmail.com

 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :
1. Fork le projet
2. Créer une branche (`git checkout -b feature/amélioration`)
3. Commit vos changements (`git commit -m 'Ajout d'une fonctionnalité'`)
4. Push (`git push origin feature/amélioration`)
5. Ouvrir une Pull Request

Support

Si vous avez des questions ou des problèmes, ouvrez une issue sur GitHub.
