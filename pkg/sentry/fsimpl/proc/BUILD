load("//pkg/sync/locking:locking.bzl", "declare_rwmutex")
load("//tools:defs.bzl", "go_library", "go_test")
load("//tools/go_generics:defs.bzl", "go_template_instance")

package(default_applicable_licenses = ["//:license"])

licenses(["notice"])

go_template_instance(
    name = "fd_dir_inode_refs",
    out = "fd_dir_inode_refs.go",
    package = "proc",
    prefix = "fdDirInode",
    template = "//pkg/refs:refs_template",
    types = {
        "T": "fdDirInode",
    },
)

go_template_instance(
    name = "fd_info_dir_inode_refs",
    out = "fd_info_dir_inode_refs.go",
    package = "proc",
    prefix = "fdInfoDirInode",
    template = "//pkg/refs:refs_template",
    types = {
        "T": "fdInfoDirInode",
    },
)

go_template_instance(
    name = "subtasks_inode_refs",
    out = "subtasks_inode_refs.go",
    package = "proc",
    prefix = "subtasksInode",
    template = "//pkg/refs:refs_template",
    types = {
        "T": "subtasksInode",
    },
)

go_template_instance(
    name = "task_inode_refs",
    out = "task_inode_refs.go",
    package = "proc",
    prefix = "taskInode",
    template = "//pkg/refs:refs_template",
    types = {
        "T": "taskInode",
    },
)

go_template_instance(
    name = "tasks_inode_refs",
    out = "tasks_inode_refs.go",
    package = "proc",
    prefix = "tasksInode",
    template = "//pkg/refs:refs_template",
    types = {
        "T": "tasksInode",
    },
)

declare_rwmutex(
    name = "dentries_mutex",
    out = "dentries_mutex.go",
    package = "proc",
    prefix = "dentries",
)

go_library(
    name = "proc",
    srcs = [
        "dentries_mutex.go",
        "fd_dir_inode_refs.go",
        "fd_info_dir_inode_refs.go",
        "filesystem.go",
        "proc_impl.go",
        "subtasks.go",
        "subtasks_inode_refs.go",
        "task.go",
        "task_fds.go",
        "task_files.go",
        "task_inode_refs.go",
        "task_net.go",
        "tasks.go",
        "tasks_files.go",
        "tasks_inode_refs.go",
        "tasks_sys.go",
        "yama.go",
    ],
    visibility = ["//pkg/sentry:internal"],
    deps = [
        "//pkg/abi/linux",
        "//pkg/atomicbitops",
        "//pkg/context",
        "//pkg/errors/linuxerr",
        "//pkg/hostarch",
        "//pkg/log",
        "//pkg/rand",
        "//pkg/refs",
        "//pkg/safemem",
        "//pkg/sentry/fsimpl/kernfs",
        "//pkg/sentry/fsimpl/lock",
        "//pkg/sentry/fsimpl/nsfs",
        "//pkg/sentry/inet",
        "//pkg/sentry/kernel",
        "//pkg/sentry/kernel/auth",
        "//pkg/sentry/ktime",
        "//pkg/sentry/limits",
        "//pkg/sentry/mm",
        "//pkg/sentry/socket",
        "//pkg/sentry/socket/unix",
        "//pkg/sentry/socket/unix/transport",
        "//pkg/sentry/usage",
        "//pkg/sentry/vfs",
        "//pkg/sync",
        "//pkg/sync/locking",
        "//pkg/tcpip/header",
        "//pkg/tcpip/network/ipv4",
        "//pkg/usermem",
        "//pkg/waiter",
    ],
)

go_test(
    name = "proc_test",
    size = "small",
    srcs = [
        "tasks_sys_test.go",
        "tasks_test.go",
    ],
    library = ":proc",
    deps = [
        "//pkg/abi/linux",
        "//pkg/context",
        "//pkg/errors/linuxerr",
        "//pkg/fspath",
        "//pkg/sentry/contexttest",
        "//pkg/sentry/fsimpl/testutil",
        "//pkg/sentry/fsimpl/tmpfs",
        "//pkg/sentry/inet",
        "//pkg/sentry/kernel",
        "//pkg/sentry/kernel/auth",
        "//pkg/sentry/vfs",
        "//pkg/usermem",
    ],
)
