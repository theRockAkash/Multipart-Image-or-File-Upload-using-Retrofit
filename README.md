# Multipart-Image-or-File-Upload-using-Retrofit

```
 private fun uploadPic(bytes: ByteArray) {
        val photoBody: MultipartBody.Part =
            MultipartBody.Part.createFormData(
                "file",
                "${System.currentTimeMillis()}.jpeg",
                bytes.toRequestBody("image/jpeg".toMediaTypeOrNull(), 0, bytes.size)
            )

val type = 2
val mediaType = "image"

        viewModel.uploadSingleImage(
            photoBody,
            type.toRequestBody("multipart/form-data".toMediaTypeOrNull()),   //extra params - type i.e 2
            mediaType.toRequestBody("multipart/form-data".toMediaTypeOrNull()) //extra params - mediaType i.e. image
        )

    }
```

#API

```
    @Multipart
    @POST("media/upload")
    suspend fun uploadSingleImage(
        @Part file: MultipartBody.Part,
        @Part("type") type: RequestBody,
        @Part("mediaType") mediaType: RequestBody,
    ): Response<SingleImageUploadResponse>


```
