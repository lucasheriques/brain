when you are developing a new product, eventually you're gonna need a few services that run async
think about this: you want your users to use your product. one of the ways to promote engagement is notifications (push or email - reference on which one is better)
you might want to send those notifications at fixed times every day

a good way to do this is by combining cronjobs and queues

cronjob will be used to add items (users) to the queue, and then we can process each queue item (users) and do what we want with them


talk about other use cases: maybe db backups? and other things