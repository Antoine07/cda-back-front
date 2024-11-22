### Atomic Design

L'Atomic Design est une méthodologie d'architecture d'interface utilisateur créée par Brad Frost. Elle s'inspire de la chimie, où les atomes se combinent pour créer des molécules, et ces molécules peuvent à leur tour se combiner pour former des organismes. L'objectif de cette approche est de créer des interfaces réutilisables, modulaires et faciles à maintenir.

Voici un petit guide pour comprendre et appliquer l'Atomic Design dans un projet React avec TypeScript.

---

### 1. **Les 5 Niveaux de l'Atomic Design**

**1. Atoms (Atomes)**

Les atomes représentent les éléments de base de l'interface. Ce sont les plus petits composants qui ne peuvent pas être décomposés davantage sans perdre leur utilité. Ce sont les boutons, les champs de texte, les icônes, les couleurs, les polices de texte, etc. Ils sont fondamentaux et servent à la construction de composants plus complexes.

- **Exemples d'atomes :**
  - Bouton
  - Champ de texte (input)
  - Icône
  - Label
  - Couleurs
  - Typographie

```tsx
// src/components/atoms/Button.tsx
export const Button = ({ label }: { label: string }) => {
  return <button>{label}</button>;
};

// src/components/atoms/Input.tsx
export const Input = ({ placeholder }: { placeholder: string }) => {
  return <input placeholder={placeholder} />;
};
```

**2. Molecules (Molécules)**

Les molécules sont des combinaisons d'atomes qui forment des éléments d'interface plus complexes et utiles. Une molécule peut contenir plusieurs atomes interconnectés. Par exemple, un champ de formulaire avec un label et un champ de saisie constitue une molécule.

- **Exemples de molécules :**
  - Formulaire avec un champ de texte et un bouton
  - Barre de recherche avec un champ de saisie et un bouton
  - Carte contenant une image et un titre

```tsx
// src/components/molecules/Form.tsx
import { Button } from '../atoms/Button';
import { Input } from '../atoms/Input';

export const Form = () => {
  return (
    <form>
      <Input placeholder="Your name" />
      <Button label="Submit" />
    </form>
  );
};
```

**3. Organisms (Organismes)**

Les organismes sont des groupes de molécules qui forment des sections complètes de l'interface utilisateur. Ils peuvent contenir des composants complexes qui sont autonomes et facilement réutilisables. Par exemple, un formulaire d'inscription complet, une navigation de site, ou une carte d'utilisateur avec des informations détaillées.

- **Exemples d'organismes :**
  - Formulaire d'inscription
  - Menu de navigation
  - Card (avec image, titre, description, bouton)
  
```tsx
// src/components/organisms/FormGroup.tsx
import { Form } from '../molecules/Form';

export const FormGroup = () => {
  return (
    <section>
      <h2>Sign Up</h2>
      <Form />
    </section>
  );
};
```

**4. Templates (Modèles)**

Les templates sont des structures plus larges qui combinent des organismes. Ils ne contiennent pas de contenu définitif, mais plutôt des "espaces réservés" pour y insérer du contenu dynamique. Ce sont des mises en page qui montrent comment les organismes et les molécules s'agencent dans une interface.

- **Exemples de templates :**
  - Template de page d'accueil avec une barre de navigation, un corps de texte, et un pied de page
  - Template de page d'article

```tsx
// src/components/templates/MainTemplate.tsx

import { Navbar } from '../organisms/Navbar';

export const MainTemplate = ( {children} ) => {
  return (
    <div>
      <Navbar />
      <main>
        {children}
      </main>
    </div>
  );
};
```

**5. Pages**

Les pages sont des instances spécifiques d'un template. Elles contiennent du contenu réel et sont ce que l'utilisateur voit. Les pages utilisent les templates pour structurer l'information et les organismes pour afficher les données spécifiques à une page.

- **Exemples de pages :**
  - Page d'accueil
  - Page de contact
  - Page d'article
  
```tsx
// src/pages/HomePage.tsx
import { MainTemplate } from '../components/templates/MainTemplate';
import { FormGroup } from '../organisms/FormGroup';

export const HomePage = () => {
  return <MainTemplate><FormGroup/></MainTemplate;
};
```

---

### 2. **Organisation des Dossiers**

Pour respecter l'Atomic Design, on peut organiser les dossiers de manière à refléter cette hiérarchie. Voici un exemple d'arborescence :

```
src/
|-- components/
|   |-- atoms/
|   |   |-- Button.tsx
|   |   |-- Input.tsx
|   |
|   |-- molecules/
|   |   |-- Form.tsx
|   |   |-- SearchBar.tsx
|   |
|   |-- organisms/
|   |   |-- FormGroup.tsx
|   |   |-- Navbar.tsx
|   |
|   |-- templates/
|   |   |-- MainTemplate.tsx
|   |
|   |-- pages/
|   |   |-- HomePage.tsx
|   |   |-- AboutPage.tsx
```

### 3. **Avantages de l'Atomic Design**

- **Réutilisabilité** : Les composants sont créés de manière à être réutilisables dans différents contextes, ce qui réduit la duplication de code et la maintenance.
- **Modularité** : Chaque composant est un bloc autonome qui peut être combiné avec d'autres pour créer des interfaces complexes.
- **Testabilité** : Les composants plus petits sont plus faciles à tester.
- **Clarté** : La séparation claire entre les différents types de composants aide à garder le code bien organisé.

### 4. **Sous-dossiers dans Atoms, Molecules, etc.**

Il est souvent utile d’organiser les composants au sein de sous-dossiers, notamment lorsque vous avez plusieurs éléments du même type. Par exemple :

```
src/
|-- components/
|   |-- atoms/
|   |   |-- buttons/
|   |   |   |-- Button.tsx
|   |   |   |-- IconButton.tsx
|   |   |
|   |   |-- inputs/
|   |   |   |-- TextInput.tsx
|   |   |   |-- PasswordInput.tsx
|   |
|   |-- molecules/
|   |   |-- forms/
|   |   |   |-- LoginForm.tsx
|   |   |   |-- SignupForm.tsx
|   |
|   |-- organisms/
|   |   |-- headers/
|   |   |   |-- MainHeader.tsx
|   |   |-- footers/
|   |   |   |-- MainFooter.tsx
```

Cela vous permet de mieux organiser vos fichiers et de rendre votre projet plus maintenable à mesure qu'il grandit.

### Conclusion

L'Atomic Design vous aide à structurer vos interfaces de manière logique et modulaire, tout en favorisant la réutilisation des composants. En appliquant cette méthodologie dans vos projets React avec TypeScript, vous pouvez construire des interfaces robustes et faciles à maintenir. L'organisation en sous-dossiers au sein des catégories comme `atoms` ou `molecules` permet également de garder une hiérarchie claire et bien structurée au sein de votre code.
