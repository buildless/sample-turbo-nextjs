# Buildless for TurboRepo

This is a [Buildless](https://less.build)-enhanced [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app), using the TurboRepo support provided by [Buildless](https://less.build) for remote caching.

## Getting Started

After installing dependencies, you can use the `turbo` (`npx turbo`) command to run your tasks, and they will be automatically stored in the remote cache:

```bash
# Run the 'build' script for the first time
npx turbo build --api="https://api.less.build/cache/turbo" --token="$BUILDLESS_API_KEY" --team="my-team"
```

If we run the task again, it will be fetched from the local cache:

```bash 
# clear the Next.js outputs
rm -fr ./.next

# run the cached task
npx turbo build --api="https://api.less.build/cache/turbo" --token="$BUILDLESS_API_KEY" --team="my-team"
>  Tasks:   1 successful, 1 total
> Cached:   1 cached, 1 total
>   Time:   14ms >>> FULL TURBO
```

To see Buildless in action, delete the local cache and re-run the build:

```bash
# clear the Next.js outputs and the local Turbo cache
rm -fr ./.next
rm -fr ./node_modules/.cache/turbo

# run the cached task, it will be fetched from Buildless!
npx turbo build --api="https://api.less.build/cache/turbo" --token="$BUILDLESS_API_KEY" --team="my-team"
>  Tasks:   1 successful, 1 total
> Cached:   1 cached, 1 total
>   Time:   63ms >>> FULL TURBO
```