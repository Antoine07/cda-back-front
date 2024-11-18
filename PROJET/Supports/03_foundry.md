 # Foundry

Si ce n'est pas déjà fait, commencez par installer **Foundry** dans votre projet Symfony :

```bash
composer require --dev zenstruck/foundry
```

---

### Étape 2 : Créer les **Factories**

#### 1. `FormationFactory`

```php
// src/Factory/FormationFactory.php
namespace App\Factory;

use App\Entity\Formation;
use Zenstruck\Foundry\ModelFactory;

class FormationFactory extends ModelFactory
{
    protected function getDefaults(): array
    {
        return [
            'name' => self::faker()->word(),
        ];
    }

    protected static function getClass(): string
    {
        return Formation::class;
    }
}
```

#### 2. `CourseFactory`

```php
// src/Factory/CourseFactory.php
namespace App\Factory;

use App\Entity\Course;
use App\Factory\FormationFactory;
use Zenstruck\Foundry\ModelFactory;

class CourseFactory extends ModelFactory
{
    protected function getDefaults(): array
    {
        return [
            'title' => self::faker()->word(),
            'formation' => FormationFactory::createOne(),
        ];
    }

    protected static function getClass(): string
    {
        return Course::class;
    }
}
```

#### 3. `ModuleFactory`

```php
// src/Factory/ModuleFactory.php
namespace App\Factory;

use App\Entity\Module;
use App\Factory\CourseFactory;
use Zenstruck\Foundry\ModelFactory;

class ModuleFactory extends ModelFactory
{
    protected function getDefaults(): array
    {
        return [
            'name' => self::faker()->word(),
            'course' => CourseFactory::createOne(),
        ];
    }

    protected static function getClass(): string
    {
        return Module::class;
    }
}
```

---

### Étape 3 : Créer les **Fixtures**

```php
// src/DataFixtures/AppFixtures.php
namespace App\DataFixtures;

use App\Factory\FormationFactory;
use App\Factory\CourseFactory;
use App\Factory\ModuleFactory;
use Doctrine\Bundle\FixturesBundle\Fixture;
use Doctrine\Persistence\ObjectManager;

class AppFixtures extends Fixture
{
    public function load(ObjectManager $manager): void
    {
        // Créer 5 formations
        $formations = FormationFactory::createMany(5);

        // Créer 10 cours
        $courses = CourseFactory::createMany(10);

        // Lier chaque cours à une formation aléatoire
        foreach ($courses as $course) {
            $course->setFormation($formations[array_rand($formations)]);
        }

        // Créer 20 modules et les lier à des cours
        ModuleFactory::createMany(20);


    }
}
```

---

### Étape 4 : Exécution des Fixtures

Pour remplir votre base de données avec les données générées, exécutez la commande suivante :

```bash
php bin/console doctrine:fixtures:load
php bin/console d:f:l
```
