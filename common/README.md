

# insighthub-common-utils

This is a utility package that provides shared types and validation schemas for both the frontend and backend of the **InsightHub Blog App**. It includes the common Zod schemas for user signup, signin, and blog management, along with their corresponding TypeScript types.

## Installation

You can install this package in your project using npm or yarn:

```bash
npm install insighthub-common-utils
```

Or with yarn:

```bash
yarn add insighthub-common-utils
```

## Usage

This package contains Zod validation schemas for common API inputs used in the **InsightHub Blog App**. It includes the following schemas:

### Signup Input Schema

The `signupInput` schema validates the data for user registration. It includes:

- **username**: A valid email address.
- **password**: A string with a minimum length of 6 characters.
- **name**: An optional field for the user's name.

```typescript
import { signupInput, SignupInput } from 'insighthub-common-utils';

const signupData: SignupInput = {
  username: 'example@example.com',
  password: 'password123',
  name: 'John Doe'
};

signupInput.parse(signupData); // This will validate the data
```

### Signin Input Schema

The `signinInput` schema validates the data for user login. It includes:

- **username**: A valid email address.
- **password**: A string with a minimum length of 6 characters.

```typescript
import { signinInput, SigninInput } from 'insighthub-common-utils';

const signinData: SigninInput = {
  username: 'example@example.com',
  password: 'password123'
};

signinInput.parse(signinData); // This will validate the data
```

### Create Blog Input Schema

The `createBlogInput` schema validates the data for creating a new blog post. It includes:

- **title**: A string for the title of the blog.
- **content**: A string for the content of the blog.

```typescript
import { createBlogInput, CreateBlogInput } from 'insighthub-common-utils';

const newBlog: CreateBlogInput = {
  title: 'My First Blog',
  content: 'This is the content of my first blog.'
};

createBlogInput.parse(newBlog); // This will validate the data
```

### Update Blog Input Schema

The `updateBlogInput` schema validates the data for updating an existing blog post. It includes:

- **title**: A string for the title of the blog.
- **content**: A string for the content of the blog.
- **id**: A number representing the unique ID of the blog post.

```typescript
import { updateBlogInput, UpdateBlogInput } from 'insighthub-common-utils';

const updatedBlog: UpdateBlogInput = {
  id: 1,
  title: 'Updated Blog Title',
  content: 'This is the updated content of the blog.'
};

updateBlogInput.parse(updatedBlog); // This will validate the data
```

## Type Inference

The package also exports TypeScript types (`SignupInput`, `SigninInput`, `CreateBlogInput`, `UpdateBlogInput`) that you can use in both your frontend and backend code to ensure type safety.

### Example: Using TypeScript Types

```typescript
import { SignupInput } from 'insighthub-common-utils';

const userData: SignupInput = {
  username: 'user@example.com',
  password: 'password123',
  name: 'John Doe'
};
```

## Contributing

Feel free to fork the repo and send a pull request if you would like to contribute. Make sure to follow the project's code style and write tests for new features.

