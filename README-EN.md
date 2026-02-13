#  Task

You need to develop a web application for expense management.

## Functional Requirements

- On the routes `/` and `/expenses`, display a list of all created expenses using the `list.html` template, and enable pagination.
  - You can verify this functionality with the tests `test_list_10pt` and `test_pagination_10pt`.

- Implement adding an expense. When clicking **Add new expense** in `list.html`, show the `form.html` template at `/expenses/add`, where clicking **Submit** creates and saves a new expense in the database. Then display `/expenses`.
  - You can verify this functionality with the tests `test_create_10pt` and `test_create_mvc_10pt`.

- Implement deleting an expense. When clicking **Delete** in `list.html`, delete the expense from the database. Then display `/expenses`.
  - You can verify this functionality with the tests `test_delete_3pt` and `test_delete_mvc_2pt`.

- Implement editing an expense. When clicking **Edit** in `list.html`, show the `form.html` template at `/expenses/edit/[id]`, with the current expense values prefilled in the `<input>` elements. When clicking **Submit**, save the changes to the database. Then display `/expenses`.
  - You can verify this functionality with the tests `test_edit_10pt` and `test_edit_mvc_10pt`.

- Implement extending the number of days until an expense expires. When clicking **Extend** in `list.html`, increase the number of days until expiration by 1. Then display `/expenses`.
  - You can verify this functionality with the tests `test_extend_3pt` and `test_extend_mvc_2pt`.

- Configure login at `/login` and logout at `/logout`. The routes `/` and `/expenses` are public, while all other pages should be visible only to a user with the `admin` role. In `list.html`, the **Edit**, **Delete**, and **Add new expense** buttons should be visible only to an `admin`, while the **Extend** button should be visible only to an authenticated user with the `user` role. 
  - You can verify this functionality with the tests `test_security_urls_10pt` and `test_security_buttons_10pt`.

- Enable searching/filtering expenses by title (whether the submitted text is contained in the `title` field), vendor, and category through the form with `id="filter-form"` in `list.html`. Results should be shown on the same page, displaying only expenses whose title contains the text and that match the selected vendor and category. Filtering is applied only for fields that are provided (empty fields are ignored).
  - You can verify this functionality with the tests `test_filter_5pt` and `test_filter_service_5pt`.

**IMPORTANT:** All mentioned tests are located in the `SeleniumScenarioTest` class.

## Submitting the Solution

You must run the tests, because that is how you submit your solution for review.  
To check whether your solution was successfully submitted, open `185.153.49.149/submit/[index]`, where you replace `[index]` with your student index, which you previously set in the `TODO` value.

The tests will help you validate correctness and will also send information to the server about how far your application works. Code will be visible only for students for whom at least one check (`ExamAssert`) passes.

**You are NOT allowed to modify the tests or any part of the `test` package, except entering your index.**  
**You MUST enter your index in the place marked with `TODO` in the `SeleniumScenarioTest` class.**

## Technical Instructions

- In `mk.ukim.finki.wp.kol2025g3.model`, the model classes are already created. You need to map them using appropriate JPA annotations so the model can be persisted in the database. The following conditions apply:
  - One expense belongs to exactly one vendor, while one vendor can be related to multiple expenses.
  - The identifiers for `Expense` and `Vendor` must be generated.

- In `mk.ukim.finki.wp.exam.kol2025g3.service`, the service interfaces are already defined. For each method there is a description of what needs to be implemented. You need to implement these interfaces in the corresponding classes in `mk.ukim.finki.wp.exam.kol2025g3.service.impl`. Additional conditions (if any) are described in the method comments.

- The classes in `mk.ukim.finki.wp.exam.kol2025g3.repository` should be extended with the required methods needed to support the service-layer functionality. They should extend Spring Data’s `JpaRepository`.

- You need to annotate the `DataInitializer` class and its methods so that `initData` runs when the application starts.

- In `mk.ukim.finki.wp.exam.kol2025g3.ExpensesController`, all required methods are defined. You need to map these handler methods using only HTTP GET and POST requests.

- Update the templates with the required Thymeleaf attributes to achieve the requested functionality. You may add missing elements and attributes, but you must NOT change the `id` and `class` attributes of existing elements.

- Configure Spring Security login and logout in the `SecurityConfig` class according to the description provided there.
