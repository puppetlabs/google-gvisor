load("//tools:defs.bzl", "go_library", "go_test")

package(licenses = ["notice"])

go_library(
    name = "sharedmem",
    srcs = [
        "queuepair.go",
        "rx.go",
        "server_rx.go",
        "server_tx.go",
        "sharedmem.go",
        "sharedmem_server.go",
        "sharedmem_unsafe.go",
        "tx.go",
    ],
    visibility = [
        "//visibility:public",
    ],
    deps = [
        "//pkg/cleanup",
        "//pkg/eventfd",
        "//pkg/log",
        "//pkg/memutil",
        "//pkg/sync",
        "//pkg/tcpip",
        "//pkg/tcpip/buffer",
        "//pkg/tcpip/header",
        "//pkg/tcpip/link/rawfile",
        "//pkg/tcpip/link/sharedmem/pipe",
        "//pkg/tcpip/link/sharedmem/queue",
        "//pkg/tcpip/stack",
        "@org_golang_x_sys//unix:go_default_library",
    ],
)

go_test(
    name = "sharedmem_test",
    srcs = ["sharedmem_test.go"],
    library = ":sharedmem",
    deps = [
        "//pkg/refs",
        "//pkg/refsvfs2",
        "//pkg/sync",
        "//pkg/tcpip",
        "//pkg/tcpip/buffer",
        "//pkg/tcpip/header",
        "//pkg/tcpip/link/sharedmem/pipe",
        "//pkg/tcpip/link/sharedmem/queue",
        "//pkg/tcpip/stack",
        "@org_golang_x_sys//unix:go_default_library",
    ],
)

go_test(
    name = "sharedmem_server_test",
    size = "large",
    srcs = ["sharedmem_server_test.go"],
    deps = [
        ":sharedmem",
        "//pkg/log",
        "//pkg/refs",
        "//pkg/refsvfs2",
        "//pkg/tcpip",
        "//pkg/tcpip/adapters/gonet",
        "//pkg/tcpip/header",
        "//pkg/tcpip/link/qdisc/fifo",
        "//pkg/tcpip/link/sniffer",
        "//pkg/tcpip/network/ipv4",
        "//pkg/tcpip/network/ipv6",
        "//pkg/tcpip/stack",
        "//pkg/tcpip/transport/tcp",
        "//pkg/tcpip/transport/udp",
        "@org_golang_x_sync//errgroup:go_default_library",
        "@org_golang_x_sys//unix:go_default_library",
    ],
)
