Default variables: configuration
================================

Some of ``ypid.divert`` variables have more extensive configuration.
Here you can find documentation and examples for them.

divert_files_list
-----------------

``original``
  Required, string. File path of the original file.

``diverted``
  Optional, string. File path where all new file versions created by package
  updates are redirected to.
  Defaults to:

  .. code:: jinja

     {{ item.original + divert_file_suffix }}

``state``
  Optional, string. If ``present``, the diversion should be enabled. If
  ``absent`` the diversion will be removed.
  Defaults to ``present``.

``copy_to_org``
  Optional, boolean. Copy the diverted file to the original file (intended when
  the file is later going to be modified without using a file template).
  Defaults to ``False``.

``force``
  Optional, boolean. If ``True`` and state is ``absent`` the diversion will be
  removed even if that means that your modified file has to be deleted first to
  restore the original version of the package maintainer.
  Defaults to ``False``.
