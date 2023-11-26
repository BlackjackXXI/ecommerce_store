# ecommerce_store

Deployed sample store: https://myecomproj-55lzbt7xm-kntjsprr.vercel.app/

## Sample env
```
# Enter url of admin api `{url}/api/{id}`
NEXT_PUBLIC_API_URL=https://ccc-admin.vercel.app/api/67dccccc-ccbf-cc3e-8cc8-cccaccca1dccc

# Paste billboard id on admin dashboard to use as default.
NEXT_BILLBOARD_ID=67dccccc-ccbf-cc3e-8cc8-cccaccca1dccc
# Enter store name
NEXT_PUBLIC_STORE_NAME=My Store
```

## Installation:
```
npm install .
npm run dev
```

## Added features/fixes
- Added Store Name on env
- Added billboard id on env


# Guide
Setup guide for e-commerce project. Make sure to setup admin first then store

### Services used
- [Railway](https://railway.app/project/) or [PlanetScale (Needs CC)](https://planetscale.com/)

- [Cloudinary](https://cloudinary.com)

- [Github](https://github.com)

- [Vercel](https://vercel.com)

- [Stripe](https://stripe.com)

- [Clerk](https://clerk.com/)

### Setting up Railway Database.
Create account on https://railway.app/project/ and create mysql project.

Go to MySQL Variable Tab and copy `MYSQL_PRIVATE_URL` and paste on the admin .env file named `DATABASE_URL`.

It should look like this: `mysql://root:DjsvAJvw@mysql.railway.internal:3306/railway`

Copy and paste code on the admin panel
```
npx prisma generate
npx prisma db push
```
### Setting up Cloudinary.
Create an account on https://cloudinary.com and copy Cloud Name to env `NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME`.

Go to [https://console.cloudinary.com/settings](https://console.cloudinary.com/settings/upload)https://console.cloudinary.com/settings/upload and click 'Add upload preset' and make it unsigned, copy the upload preset name and click save and then paste it to env key `NEXT_PUBLIC_CLOUDINARY_UPLOAD_PRESET_NAME` value.

### Setting up Clerk.
Go to https://dashboard.clerk.com/ and create an account.
Create a project and go to API Keys and copy the value of `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` & `CLERK_SECRET_KEY` and paste it on .env accordingly.

### Deploying application
Before deploying make sure that `FRONTEND_STORE_URL` is blank and `STRIPE_API_KEY` and `STRIPE_WEBHOOK_SECRET`.

Create an account to github and vercel.

Upload the admin project and deploy on vercel.

Copy all .env contents of the admin project to vercel.

Login to the admin panel and create a store.

Go to store settings and copy the value of `NEXT_PUBLIC_API_URL` and paste to store's .env `NEXT_PUBLIC_API_URL`.

Upload the store project to github and deploy to vercel. Don't forget to copy all store .env contents to vercel.

Setup the domain if applicable and then copy the domain url to `FRONTEND_STORE_URL` from admin vercel .env (NO SLASHES AT THE END).

Create billboard from admin dashboard and then copy the billboard id and paste it to **store's** vercel .env and change store name as well on .env.

### Setting up stripe
Sign up to https://dashboard.stripe.com/ and copy stripe secret key to `STRIPE_API_KEY` admin project's vercel .env file.

Create a stripe webhook endpoint and put (ADMIN_URL.vercel.app)/api/webhook and listen to `checkout.session.completed` event.

Copy Stripe Signing secret to vercel admin panel .env. It should look like this: `whsec_yj...`


## Test stripe purchase
Go buy anything and use the test card 424242424242 and use anything for exp and cvc.

Test if webhook working and everything.

You're good to go, Now you can setup social media's for stripe marketing.
