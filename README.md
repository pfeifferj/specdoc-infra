# specdoc-infra

cluster manifests for [specdoc](https://github.com/pfeifferj/specdoc)

the editor and board require the `spec-board-editor` secret in the `hedgedoc`
namespace, with a cryptographically random value under `token`. provision it
before applying the app manifests. both deployments reference the same key for
signed approval assertions and editor mutations, including bot comments. the
board reaches the editor through its internal service address.

The netfyr deployment is managed by [netfyr/infra](https://github.com/netfyr/infra).
Its `terraform/specs` root owns the public board and editor origins, namespace
selection, board image trigger and editor routing, including the legacy Ingress.
A fresh installation needs that deployment configuration before serving traffic.

For existing installations, follow the [field ownership handoff](https://github.com/netfyr/infra/blob/main/docs/deployment.md#specdoc-field-ownership)
before applying these manifests. Apply base updates server-side without forcing
conflicts or pruning resources. Keep the deployment's reviewed image in the
rendered manifest; the image digests here are bootstrap values. An image conflict
requires reconciling the rendered configuration with the running deployment.
