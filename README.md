# Forms and Tables

## About

This is the homework solution for the Forms and Tables topics, based on the task below.

This homework covers following topics:
* forms and form elements
* pseudo-classes for form elements
* tables

The solution includes markup and corresponding CSS styles.

A JS script has been provided that manages the opening and closing of the modal window.

### Module objectives

* To understand what HTML forms are and how they work.
* To distinguish the main types of elements in forms (form, label, input, etc.).
* To stylize forms on a page.
* To be able to group related form elements.
* To create different types of forms.
* To apply a set of special pseudo-classes for form elements.
* To know tags for creating tables and be able to group cells in tables.

## Task

* Add markup and forms design as indicated on the [Homework #5 layout](https://www.figma.com/file/Kr5Q4EVrEAqpOWko4QeEJb/Web-Studio-(Version-4.0)?type=design&node-id=297035-1582&t=xehgKGCXNQoohzws-0).
* Set up GitHub Pages and add a live page to the header of the GitHub repository.
* The solution must meet the mentor's acceptance criteria.

## Useful information and insights

* <details>
  <summary>Change input icon color usin adjacent sibling selector (E1 + E2).</summary>
  
  1. Create `label` and `input` elements with icon.
      
      `position:absolute` not working on `input`, so use additional wrapper around `input` and `svg`.

      Be aware, that `div` cant be included into `label`, use `span` instead to wrap elements.

      Position icon as absolute to Use sibling selector (E1 + E2) to change icon styles.

      ```html
      <form class="order-form">
        <label class="order-form-field-username order-form-field">
          <p class="order-form-field-description">Name</p>
          <span class="order-form-input-wrapper">
            <input class="order-form-field-input order-form-interactive-text-element" type="text" name="user_name"
              pattern="" title="" required>
            <svg class="order-form-field-input-icon" width="12" height="12">
              <use href="./images/icons.svg#icon-person"></use>
            </svg>
          </span>
        </label>
      </form>
      ```

      ```css
      .order-form-input-wrapper {
        display: block;
        position: relative;
      }

      .order-form-field-input {
        height: 40px;
        padding-left: 38px;
      }

      .order-form-field-input-icon {
        position: absolute;
        top: 50%;
        left: 25px;
        transform: translate(-50%, -50%);
        fill: var(--modal-window-element-color-dark);
        transition: fill var(--transition-duration) var(--transition-duration);
      }

      .order-form-field-input:focus + .order-form-field-input-icon {
        fill: var(--brand-color);
      }
      ```
  </details>
* <details>
  <summary>Create custom checkmark and hide original.</summary>

  1. Create checkbox and custom mark using custom icon and place it near.
      ```html
      <label class="order-form-field-terms order-form-field">
        <input class="order-form-terms-checkbox" type="checkbox" name="" value="accepted" required>
        <span class="order-form-terms-custom-checkmark">
          <svg class="order-form-terms-custom-checkmark-icon" width="10" height="8">
            <use href="./images/icons.svg#icon-checkmark"></use>
          </svg>
        </span>
        I accept the terms and conditions of&nbsp;
        <a href="" class="order-form-terms-link" target="_blank">Privacy Policy</a>
      </label>
      ```
  2. Use sibling rules to imitate interactive element behavoir.
      ```css
      .order-form-terms-checkbox:checked + .order-form-terms-custom-checkmark {
        border: none;
        background-color: var(--active-element-color);
      }

      .order-form-terms-checkbox:focus + .order-form-terms-custom-checkmark {
        outline: 1px solid var(--brand-color);
        outline-offset: 2px;
      }

      .order-form-terms-custom-checkmark-icon {
        display: block;
        fill: transparent;
        transition: fill var(--transition-duration) var(--transition-function);
      }

      .order-form-terms-checkbox:checked + .order-form-terms-custom-checkmark
      > .order-form-terms-custom-checkmark-icon {
        fill: var(--secondary-accent-color);
      }
      ```
  3. Hide original checkbox.
      ```css
      .order-form-terms-checkbox {
        position: absolute;
        appearance: none;
      }
      ```
  
  </details>
