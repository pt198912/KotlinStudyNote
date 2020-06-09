# KotlinStudyNote
1、kotlin泛型函数实例

     fun <D:Operation.Data,T:Operation.Data,V:Operation.Variables,Q : Query<D, T, V>> query(q:                  Q,myCallback:ApolloCall.Callback<T>?) {
            val apolloCall: ApolloQueryCall<T>? = apolloClient?.query(q)
            apolloCall?.enqueue(object : ApolloCall.Callback<T>() {
                override fun onResponse(response: Response<T>) {
                    val data = response.data()
                    myCallback?.onResponse(response)
                    Log.d(TAG, "apollo onResponse: ")
                }

                override fun onFailure(e: ApolloException) {
                    Log.d(TAG, "apollo onFailure: ")
                    myCallback?.onFailure(e)
                }
            })
        }
