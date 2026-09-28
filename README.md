# specdoc-infra

cluster manifests for [specdoc](https://github.com/pfeifferj/specdoc)

the editor and board require the `spec-board-editor` secret in the `hedgedoc`
namespace, with a cryptographically random value under `token`. provision it
before applying the app manifests. both deployments reference the same key for
signed approval assertions and editor mutations, including bot comments. the
board reaches the editor through its internal service address.
