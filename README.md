# tinyland-user-resolution (retired)

**Retired 2026-10-14 (RU2, RU7).** This module was merged into
[`xoxd-ai/tinyland-content`](https://github.com/xoxd-ai/tinyland-content) and
this repository is archived. Nothing here receives updates.

## Replacement

- Bazel module: `tummycrypt_tinyland_content` 1.1.0 or later, from the
  Tinyland Bazel registry (`xoxd-ai/bazel-registry`). Bazel is the only
  distribution path (RU6).
- Import path: `@tummycrypt/tinyland-content/user-resolution`, with the same
  API as 0.2.3: `configure`, `getConfig`, `resetConfig`, `resolveUser`,
  `userExists`, `getAllUserHandles`, `clearUserResolutionCache`,
  `RESERVED_ROUTES`, `isReservedRoute` and the `AdminUser`, `Profile`,
  `ResolvedUser` and `UserResolutionConfig` types. The root
  `@tummycrypt/tinyland-content` facade also exports them as
  `configureUserResolution`, `getUserResolutionConfig`,
  `resetUserResolutionConfig`, `getAllUserHandlesFromResolution`,
  `resolveUser`, `userExists`, `clearUserResolutionCache`, `RESERVED_ROUTES`
  and `isReservedRoute` (the `Profile` input type is only on the subpath).
- Tests: the TIN-2788 directory-authority cases from #16 ship with the merged
  suite in tinyland-content.

## Migration

1. Drop `bazel_dep(name = "tummycrypt_tinyland_user_resolution", ...)`, any
   `single_version_override` for it and its `npm_link_package`.
2. Depend on `bazel_dep(name = "tummycrypt_tinyland_content", version = "1.1.0")`
   or later.
3. Replace `from '@tummycrypt/tinyland-user-resolution'` with
   `from '@tummycrypt/tinyland-content/user-resolution'`. Use the same
   specifier everywhere in an app: `configure()` state is per module instance.

## Existing versions

- Bazel registry: `tummycrypt_tinyland_user_resolution` 0.2.2 and 0.2.3 stay
  resolvable and are marked deprecated. Nothing is yanked.
- npm: no new versions will be published. Existing
  `@tummycrypt/tinyland-user-resolution` versions are not unpublished; their
  deprecation pointer is an operator step (RU8).
