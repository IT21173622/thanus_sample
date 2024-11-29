Please go under edit and edit this file as needed for your project.  There is no seperate documentation needed.

# Project Name - Cooking Master
# Student Id - IT21311840
# Student Name - Rizan S

Cooking Master - Recipe Management App
Cooking Master is a SwiftUI-based mobile app that allows users to manage, view, add, edit, and delete recipes. The app enables users to store recipes with key information like ingredients, steps, cooking time, and images. It also provides an easy-to-use interface for discovering, creating, and sharing recipes

01. Brief Description of Project
Cooking Master is a mobile application designed to help users store and organize their favorite recipes. With features such as adding new recipes, editing existing ones, deleting outdated recipes, and uploading images, the app provides a comprehensive solution for recipe management. The app utilizes SwiftUI for the user interface and integrates features like photo selection and real-time recipe updates.

02. Users of the System
1. Home Cooks
Description: Home cooks are the primary target audience for the app. These users enjoy experimenting with recipes, trying out new dishes, and organizing their culinary creations in a digital format.
Use Cases:
Adding new recipes they discover or create.
Editing recipes for future modifications (e.g., adjusting ingredients or cooking time).
Viewing their saved recipes quickly when cooking.
Deleting recipes that are no longer needed or relevant.
Uploading images of their dishes to better visualize the recipe.
2. Professional Chefs or Culinary Enthusiasts
Description: These users might be more experienced in the kitchen and use the app to store their signature recipes, experiment with new dishes, or even organize their recipes by course, cuisine, or occasion.
Use Cases:
Organizing large collections of recipes for different cuisines or special occasions.
Editing and modifying existing recipes to improve or personalize them.
Uploading high-quality images of their dishes to share with others.
Deleting recipes that are outdated or no longer in use

03. What is Unique About Your Solution
Cooking Master is unique in the following ways:

Comprehensive Recipe Management: Unlike other recipe apps, Cooking Master allows users to manage not only the text-based recipe content (ingredients and steps) but also supports rich media, such as uploading images.
Image Integration: The app integrates an image picker, which allows users to capture or upload images directly from their photo library, helping users visualize the recipe more clearly.
Simple UI: The app leverages SwiftUI to provide a clean, intuitive, and visually appealing interface, making it easier for users to interact with the app.


04. Briefly Document the Functionality of the Screens You Have
Screen 1: Recipe List
This is the main screen where users can see a list of all the recipes they’ve added. It displays each recipe's name and a preview image. Users can navigate to individual recipe details by tapping on a recipe. They can also add new recipes by tapping the "Add Recipe" button.

Screen 2: Recipe Detail
This screen shows detailed information about a selected recipe, including its name, cooking time, ingredients, steps, and an image. Users can edit or delete the recipe from this screen by tapping the respective buttons. Editing will take them to the Add Recipe screen, where they can make changes and save them.

Screen 3: Add/Edit Recipe
This screen is used to add a new recipe or edit an existing one. Users can input the recipe name, cooking time, ingredients, and steps, as well as upload an image of the dish. The form also includes a button to pick an image from the photo library. Once the details are filled out, users can save the recipe.

05. Best Practices Used When Writing Code
Consistent Naming Conventions: The code follows a clear and consistent naming convention for variables, functions, and struct names. For example, the struct Recipe clearly represents a recipe, and methods like addRecipe and deleteRecipe use action-based verbs to clearly define their functionality.

Modularization: The code is structured in a way that allows easy reusability of components. For example, the ImagePicker is encapsulated in a separate view, making it reusable for different parts of the app.

![Screen 1](Resources/screen01.png)  

#### 05. Give examples of best practices used when writing code
e.g The code below uses consistant naming conventions for variables, uses structures and constants where ever possible. (Elaborate a bit more on what you did)

struct Recipe {
    let name: String
    let cookingTime: Int
    let ingredients: [String]
    let steps: [String]
    let imageData: Data?

    init(name: String, cookingTime: Int, ingredients: [String], steps: [String], imageData: Data? = nil) {
        self.name = name
        self.cookingTime = cookingTime
        self.ingredients = ingredients
        self.steps = steps
        self.imageData = imageData
    }
}

```

#### 06. UI Components used

The following UI components were used in the Cooking Master app:

TextField: Used for input fields like recipe name and cooking time.
Button: Used for actions like adding, editing, and deleting recipes.
ImagePicker: Custom view that allows users to select an image from the photo library.
ScrollView: For displaying content that may exceed the screen height, such as long recipe lists or detailed recipe steps.

#### 07. Testing carried out

Testing focused on validating that the core functionality of the app works correctly, including adding, editing, and deleting recipes. Below is a sample test class used to test the Recipe Manager.

```
    class RecipeManagerTests: XCTestCase {

    var recipeManager: RecipeManager!
    
    override func setUp() {
        super.setUp()
        recipeManager = RecipeManager()
    }

    func testAddRecipe() {
        let recipe = Recipe(name: "Pasta", cookingTime: 30, ingredients: ["Pasta", "Tomato Sauce"], steps: ["Boil water", "Cook pasta", "Add sauce"])
        recipeManager.addRecipe(recipe)
        XCTAssertTrue(recipeManager.recipes.contains(where: { $0.name == "Pasta" }))
    }

    func testDeleteRecipe() {
        let recipe = Recipe(name: "Pasta", cookingTime: 30, ingredients: ["Pasta", "Tomato Sauce"], steps: ["Boil water", "Cook pasta", "Add sauce"])
        recipeManager.addRecipe(recipe)
        recipeManager.deleteRecipe(recipe)
        XCTAssertFalse(recipeManager.recipes.contains(where: { $0.name == "Pasta" }))
    }
}

```

#### 08. Documentation 

(a) Design Choices
Architecture: The app follows the Model-View-ViewModel (MVVM) architecture, with clear separation between the UI and data models. This makes it easier to maintain and extend the app.
Data Persistence: For simplicity, the app stores recipes in memory, but this can be extended to use CoreData or an external database in future versions.

(b) Implementation Decisions
Image Handling: The app uses the UIImagePickerController to allow users to pick images from their photo library, simplifying image selection.
User Interface: SwiftUI was chosen for the UI to take advantage of its declarative nature and automatic handling of UI updates.

(c) Challenges
Handling Image Uploads: One challenge was ensuring that images were correctly uploaded and displayed even when the data was in an optional state.
Editing Functionality: Initially, there were issues with updating the recipe data correctly when editing, which was solved by ensuring that all data is passed and updated correctly through the state binding mechanism.

#### 09. References and All GenAI Prompts and Responses that you got

GenAI Response:
GenAI suggested using the UIImagePickerController for image selection, wrapped inside a UIViewControllerRepresentable to integrate it with SwiftUI. It also recommended handling image data using a @State variable to store the selected image.

Usage in Project:
The image upload functionality in the app was implemented based on this response, allowing users to select images from their device's photo library and associate them with a recipe.



#### 10. Reflection

Challenges Faced: One of the main challenges was handling image uploads and ensuring that the images were correctly stored and displayed when editing recipes. The app required dealing with optional image data, which was tricky at first.

  

