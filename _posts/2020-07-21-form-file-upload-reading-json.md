---
layout: post
title: "Creating a Upload form field and retrieving JSON content in Drupal 8"
date: 2020-07-21
---
Upload field in a form can be added directly in `buildForm` method of Form class or using a `hook_form_alter`.

```php
$form['json_upload'] = [
      '#type' => 'managed_file',
 *     '#title' => $this->t('JSON file upload'),
      '#upload_location' => 'public://importjson/',
      '#default_value' => '',
      "#upload_validators"  => ["file_validate_extensions" => ["json"]],
      '#states' => [
        'visible' => [
          ':input[name="File_type"]' => ['value' => $this->t('Upload Your File')],
        ],
      ],
    ];
 ```
 The `file_validate_extensions` in `upload_validators` would only allow `json` file to upload.
 
 **Retrieving the JSON file content**
 ```php
 $fid = $form_state->getValue('json_upload');
 $json_file = $this->fileStorage->load($fid[0]);
      $file_content = json_decode(file_get_contents($json_file->getFileUri()));
      if (empty($file_content)) {
        drupal_set_message($this->t('Please upload a file with content.'), 'error'); return;
      }
 ```
 
